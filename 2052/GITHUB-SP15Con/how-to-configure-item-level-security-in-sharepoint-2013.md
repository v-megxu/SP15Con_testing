---
title: 如何：在 SharePoint 2013 中配置项目级安全性
ms.prod: SHAREPOINT
ms.assetid: ffd730f2-e7b7-4707-b677-d073da7df7d7
---


# 如何：在 SharePoint 2013 中配置项目级安全性
学习如何在使用 SharePoint 2013 中的 BCS 索引连接器对外部数据进行爬网时配置项目级安全。
## 具有 NTLM 身份验证的外部系统
<a name="ItemLevelSecurity_NTLMAuth"> </a>

对于支持 NTLM 身份验证的外部系统来说，可以在爬网时间为外部内容类型的每个实例获取安全描述符，并将其存储在内容索引中。在查询期间，把正在提交搜索查询的用户的安全描述符与存储的安全描述符相比较，以确定该用户是否可以对该项进行访问。这是在结果集中执行安全修整的最快方式。 外部系统的元数据模型必须指示在什么地方可以发现安全描述符为外部内容类型或方法。
  
    
    

### 外部内容类型字段
<a name="ItemLevelSecurity_ExtTypeField"> </a>

如果使用 **WindowsSecurityDescriptorField** 属性对包含该描述符的外部内容类型字段进行了标记，则 Microsoft SharePoint 2013 将存储该安全描述符（如以下示例所示）。
  
    
    

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


> **注释**
> 如果您返回安全描述符为外部内容类型字段，那么您将不能使用客户端缓存。因为已缓存的项限于特定大小，访问控件列表 (ACL) 可以轻易超过。因此，如果它们包含了安全描述符字符，搜索 连接器框架将忽略对缓存项的请求。 
  
    
    


### 外部内容类型方法
<a name="ItemLevelSecurity_ExtTypeMethod"> </a>

如果您在基于其标识符返回项的安全描述符的元数据模型中定义了方法，则您可以使用 **BinarySecurityDescriptorAccessor** 构造型（如以下示例所示）。
  
    
    

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

以下代码是上一个示例中指定的方法的方法签名。
  
    
    



```cs

Public static Byte[]GetItemSecurity (string  id)
{

}
```


## 具有可以映射到 NTLM 身份验证的身份验证方案的外部系统
<a name="ItemLevelSecurity_MappedToNTLM"> </a>

如果该外部系统不支持 NTLM 身份验证，但是可以使用映射表将外部系统用户映射到 Windows 用户，那么您将可以使用上两个代码示例中描述的方法来提供项目级安全。 为了让此工作，外部系统揭示的 Web 服务或 Windows Communication Foundation (WCF) 服务必须包括这样一种方法，使用这种方法可以将外部系统用户内部转换为 Windows 用户，然后为每个 URL 返回 Windows 安全描述符。以下示例演示了您如何针对此方法进行编码。 
  
    
    

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


## 其他资源
<a name="SP15Itemlevelsec_addlresources"> </a>


-  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [实现 BinarySecurityDescriptorAccessor](http://msdn.microsoft.com/library/6cf70490-dd3c-49cd-bb13-ed33e938435d%28Office.15%29.aspx)
    
  
-  [增强 SharePoint 2013 中的搜索功能的 BDC 模型文件](enhancing-the-bdc-model-file-for-search-in-sharepoint-2013.md)
    
  

