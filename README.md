# T4
根据Model层的edmx文件 来生成各个层所需要的代码。
##核心
```csharp
<#
CodeGenerationTools code = new CodeGenerationTools(this);
MetadataLoader loader = new MetadataLoader(this);
CodeRegion region = new CodeRegion(this, 1);
MetadataTools ef = new MetadataTools(this);

string inputFile = @"..\\MyBlog.Model\\MyBlog.edmx";

EdmItemCollection ItemCollection = loader.CreateEdmItemCollection(inputFile);
string namespaceName = code.VsNamespaceSuggestion();

EntityFrameworkTemplateFileManager fileManager = EntityFrameworkTemplateFileManager.Create(this);

#>
//遍历所有model
<#foreach (EntityType entity in ItemCollection.GetItems<EntityType>().OrderBy(e => e.Name))
{#>
    <#=entity.Name#> //model的名称
<#}#>
```
