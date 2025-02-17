+++
title = "azure_web_app_function Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_web_app_function"
identifier = "inspec/resources/azure/azure_web_app_function Resource"
parent = "inspec/resources/azure"
+++

Use the `azure_web_app_function` InSpec audit resource to test properties related to a Azure function .

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

`resource_group` and `site_name` and `function_name` or the `resource_id` must be given as a parameter.
```ruby
describe azure_web_app_function(resource_group: resource_group, site_name: site_name, function_name: function_name) do
  it                                      { should exist }
  its('name')                             { should cmp "#{site_name}/#{function_name}" }
  its('type')                             { should cmp 'Microsoft.Web/sites/functions' }
  its('properties.name')                  { should cmp function_name }
  its('properties.language')              { should cmp 'Javascript' }
end
```
```ruby
describe azure_web_app_function(resource_id: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Web/sites/{siteName}/functions/{functionName}') do
  it            { should exist }
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in. `MyResourceGroup`.

`name`
: Name of the Azure Function App to test. `FunctionApp`.

`site_name`
: Name of the Azure Function App to test (for backward compatibility). `FunctionApp`.

`function_name`
: Name of the Azure Function to test `Function`.

`resource_id`
: The unique resource ID. `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Web/sites/{siteName}/functions/{functionName}`.

Either one of the parameter sets can be provided for a valid query:
- `resource_id`
- `resource_group` and `name` and `function_name`
- `resource_group` and `site_name` and `function_name`

## Properties

`config_href`
: Config URI.

`function_app_id`
: Function App ID.

`language`
: The function language.

`isDisabled`
: Gets or sets a value indicating whether the function is disabled.

For properties applicable to all resources, such as `type`, `name`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/appservice/webapps/getfunction#functionenvelope) for other properties available.
Any attribute in the response may be accessed with the key names separated by dots (`.`).

## Examples

**Test <>.**

```ruby
describe azure_web_app_function(resource_group: 'MyResourceGroup', site_name: 'functions-http', function_name: 'HttpTrigger1') do
  its('properties.language') { should eq 'Javascript' }
end
```
**Test <>.**

```ruby
describe azure_web_app_function(resource_group: 'MyResourceGroup', site_name: 'functions-http', function_name: 'HttpTrigger1') do
  its('properties.isDisabled') { should be_false }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](/inspec/matchers/).

### exists

```ruby
# If a key vault is found it will exist

describe azure_web_app_function(resource_group: 'MyResourceGroup', site_name: 'functions-http', function_name: 'HttpTrigger1') do
  it { should exist }
end

# Key vaults that aren't found will not exist
describe azure_web_app_function(resource_group: 'MyResourceGroup', site_name: 'functions-http', function_name: 'HttpTrigger1') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal role="contributor" %}}
