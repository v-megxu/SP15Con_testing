---
title: 方法 SharePoint 2013 でアイテム レベルのセキュリティを構成する
ms.prod: SHAREPOINT
ms.assetid: ffd730f2-e7b7-4707-b677-d073da7df7d7
---


# 方法: SharePoint 2013 でアイテム レベルのセキュリティを構成する
SharePoint 2013で BCS インデックス コネクタを使用して外部データをクロールする際に、アイテム単位でセキュリティを設定する方法を説明します。
## NTLM 認証を使用する外部システム
<a name="ItemLevelSecurity_NTLMAuth"> </a>

NTLM 認証をサポートする外部システムでは、クロール時に、外部コンテンツ タイプのインスタンスごとにセキュリティ記述子を取得して、コンテンツ インデックスに格納できます。クエリ時には、検索クエリを送信したユーザーのセキュリティ記述子が、格納されたセキュリティ記述子と比較され、ユーザーがアイテムにアクセスできるかどうかが確認されます。これが、結果セット上でセキュリティ トリミングを最も短時間で実行する方法です。外部システムのメタデータ モデルでは、外部コンテンツ タイプ フィールドまたはメソッドとしてセキュリティ記述子が含まれている場所が示される必要があります。
  
    
    

### 外部コンテンツ タイプ フィールド
<a name="ItemLevelSecurity_ExtTypeField"> </a>

次の例のように、セキュリティ記述子を含む外部コンテンツ タイプのフィールドが、 **WindowsSecurityDescriptorField** プロパティを使用してマーク付けされている場合、Microsoft SharePoint 2013はそのセキュリティ記述子を格納します。
  
    
    

```XML

<Method Name="Item SpecificFinder ">
  <Properties>
    <Property Name="RdbCommandType" Type="System.Data.CommandType, System.Data, 
 Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">Text</Property>
    <Property Name="RdbCommandText" Type="System.String">SELECT [Identifier] , 
 [SecurityDescriptor] FROM [Test].[dbo].[Items] WHERE [Identifier] = @Identifier</Property>
    <Property Name="BackEndObjectType" Type="System.String">SqlServerTable</Property>
    <Property Name="BackEndObject" Type="System.String">Items</Property>
    <Property Name="Schema" Type="System.String">dbo</Property>
  </Properties>
  <Parameters>
    <Parameter Direction="In" Name="@Identifier">
      <TypeDescriptor TypeName="System.Int32" IdentifierName="Identifier" Name="Identifier" />
    </Parameter>
    <Parameter Direction="Return" Name="BaseItemsRead Item">
      <TypeDescriptor TypeName="System.Data.IDataReader, System.Data, Version=2.0.0.0, 
Culture=neutral, PublicKeyToken=b77a5c561934e089" IsCollection="true" Name="BaseItemsRead Item">
        <TypeDescriptors>
          <TypeDescriptor TypeName="System.Data.IDataRecord, System.Data, Version=2.0.0.0, 
Culture=neutral, PublicKeyToken=b77a5c561934e089" Name="BaseItemsRead ItemElement">
          <TypeDescriptors>
            <TypeDescriptor TypeName="System.Int32" IdentifierName="Identifier" Name="Identifier"/>
            <TypeDescriptor TypeName="System.Byte[], mscorlib, Version=2.0.0.0, 
Culture=neutral, PublicKeyToken=b77a5c561934e089" IsCollection="true" Name="SecurityDescriptor">
              <TypeDescriptors>
                <TypeDescriptor TypeName="System.Byte" Name="SecurityDescriptorElement" />
              </TypeDescriptors>
            </TypeDescriptor>
            </TypeDescriptors>
          </TypeDescriptor>
          </TypeDescriptors>
        </TypeDescriptor>
      </Parameter>
    </Parameters>
    <MethodInstances>
      <MethodInstance Type="SpecificFinder" ReturnParameterName="BaseItemsRead Item"
 ReturnTypeDescriptorName="BaseItemsRead ItemElement" Name="BaseItemsRead Item"
DefaultDisplayName="ReadSecurity">
        <Properties>
          <Property Name="WindowsSecurityDescriptorField" Type="System.String">
                SecurityDescriptor
          </Property>
        </Properties>
      </MethodInstance>
    </MethodInstances>
</Method>
```


> **メモ**
> セキュリティ記述子を外部コンテンツ タイプのフィールドとして返す場合、クライアント キャッシュを使用できません。これは、キャッシュされたアイテムが特定のサイズに制限されるためです。アクセス制御リスト (ACL) は、このサイズを簡単に超える可能性があります。したがって、キャッシュ アイテムへの要求にセキュリティ記述子フィールドが含まれる場合、検索 コネクタ フレームワークではその要求は無視されます。 
  
    
    


### 外部コンテンツ タイプ メソッド
<a name="ItemLevelSecurity_ExtTypeMethod"> </a>

ID に基づいてアイテムのセキュリティ記述子を返すメソッドがメタデータ モデルに定義されている場合、次の例のように、 **BinarySecurityDescriptorAccessor** メソッドのステレオタイプを使用できます。
  
    
    

```XML

<Method Name="GetItemSecurity" LobName="GetItemSecurity">
  <Parameters>
    <Parameter Name="itemId" Direction="In">
      <TypeDescriptor Name="itemId" TypeName="System.Int32, mscorlib, 
Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" 
IdentifierEntityNamespace="MS.Internal.Test.Automation.Search.Scater" 
IdentifierEntityName="Item" IdentifierName="ItemId" /> 
    </Parameter>
    <Parameter Name="Return" Direction="Return">
      <TypeDescriptor Name="SecurityDescriptor" TypeName="System.Byte[],
mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" 
IsCollection="true">
        <TypeDescriptors>
          <TypeDescriptor Name="Item" TypeName="System.Byte, mscorlib, 
Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
        </TypeDescriptors>
      </TypeDescriptor>
    </Parameter>
  </Parameters>
  <MethodInstances>
    <MethodInstance Name="GetItemSecurity_Instance" Type="BinarySecurityDescriptorAccessor"
 ReturnParameterName="Return" ReturnTypeDescriptorName="SecurityDescriptor" 
ReturnTypeDescriptorLevel="0">
      <Properties>
        <Property Name="WindowsSecurityDescriptorField" Type="System.String">
            SecurityDescriptor
        </Property>
      </Properties>
      <AccessControlList>
        <AccessControlEntry Principal="NT AUTHORITY\\Authenticated Users">
          <Right BdcRight="Execute" />
        </AccessControlEntry>
      </AccessControlList>
    </MethodInstance>
  </MethodInstances>
</Method>
```

次のコードは、前の例に指定されたメソッドのメソッド署名です。
  
    
    



```cs

Public static Byte[]GetItemSecurity (string  id)
{

}
```


## NTLM 認証へのマッピングが可能な認証スキームを使用する外部システム
<a name="ItemLevelSecurity_MappedToNTLM"> </a>

NTLM 認証がサポートされていない外部システムで、マッピング テーブルを使用して外部システムのユーザーを Windows ユーザーにマッピングできる場合、前の 2 つのコード例に示された方法を使用して、アイテム レベル セキュリティを実現できます。これを正常に動作するには、外部システムのユーザーを Windows ユーザーに内部的に変換し、URL ごとに Windows セキュリティ記述子を返すメソッドが、外部システムで公開されている Web サービスまたは Windows Communication Foundation (WCF) サービスに含まれる必要があります。次の例は、このメソッドのコーディング方法を示しています。 
  
    
    

```cs

/// Returns the security descriptor for a user.
/// </summary>
/// <param name="domain"></param>
/// <param name="username"></param>
/// <returns></returns>

private Byte[] GetSecurityDescriptor(string domain, string username)
{
   NTAccount acc = new NTAccount(domain, username);
   SecurityIdentifier sid = (SecurityIdentifier)acc.Translate(typeof(SecurityIdentifier));
   CommonSecurityDescriptor sd = new CommonSecurityDescriptor(false, false, ControlFlags.None,
sid, null, null, null);
   sd.SetDiscretionaryAclProtection(true, false);

//Deny access to all users.
   SecurityIdentifier everyone = new SecurityIdentifier(WellKnownSidType.WorldSid, null);
   sd.DiscretionaryAcl.RemoveAccess(AccessControlType.Allow, everyone, 
unchecked((int)0xffffffffL), InheritanceFlags.None, PropagationFlags.None);

//Grant full access to a specified user.
   sd.DiscretionaryAcl.AddAccess(AccessControlType.Allow, sid, 
unchecked((int)0xffffffffL), InheritanceFlags.None, PropagationFlags.None);
 
   byte[] secDes = new Byte[sd.BinaryLength];
   sd.GetBinaryForm(secDes, 0);

   return secDes;
}
```


## その他の技術情報
<a name="SP15Itemlevelsec_addlresources"> </a>


-  [SharePoint 2013 の検索コネクタ フレームワーク](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [BinarySecurityDescriptorAccessor の実装](http://msdn.microsoft.com/library/6cf70490-dd3c-49cd-bb13-ed33e938435d%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の検索用 BDC モデル ファイルを強化する](enhancing-the-bdc-model-file-for-search-in-sharepoint-2013.md)
    
  

