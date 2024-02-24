# Flow of compiling a mMojo using KRN Core

<img width="668" alt="image" src="https://github.com/krn-sebastiaan/krn-sebastiaan/assets/159554287/d4e177dc-980c-4f28-875e-d9d2d31c50fc">

The above flow is provided using [this GitHub Action](https://github.com/krn-sebastiaan/actions/blob/main/compile/action.yml). Please read the [README](https://github.com/krn-sebastiaan/actions/blob/main/README.md) for more information.   
For installing SW Core, MUnit and KRN Core, [this GitHub Action](https://github.com/krn-sebastiaan/krn-core) is used.  
The artifact itself is uploaded to the workflow run in GitHub.

# Flow of releasing a mMojo using KRN Core

The flow for releasing a mMojo, is an extension from the above flow for compiling a mMojo. This is provided using [this GitHub Action](https://github.com/krn-sebastiaan/actions/blob/main/release/action.yml).  
It adds an extra step to publish the artifacts to a GitHub release.

# Providing mMojos

We can provide mMojos using a `repositories.xml`. An example is provided in [this repository](https://github.com/krn-sebastiaan/mmojo-repositories).
When a Smallworld product requires another product (e.g. MUnit), we must make sure this one is built already and can be downloaded.

```xml
<repositories>
	<repo name="Keronic GitHub Repository">
		<get url="https://krn-sebastiaan.github.io/mmojos-store"/>
	</repo>
</repositories>
```

The url provided for the repository, needs to have a [`mojos.xml`](https://github.com/krn-sebastiaan/mmojos-store/blob/main/mojos.xml) in the root-folder.
For setting up a repository to provide mMojos, there is a [template repository](https://github.com/krn-sebastiaan/mmojos-store-template) available.
The `mojos.xml` lists the available mMojos:

```xml
<registry>
	<mojo>
		<name>a_mojo</name>
		<version>1.0.0</version>
		<file>a_mojo/a_mojo-1.0.0.jar</file>
		<description>A description about the mMojo</description>
		<product name="a_mojo" version="1.0.0"/>
		<requires>
			<product name="another_sw_product_name" version="1.0"/>
			...
		</requires>
	</mojo>
</registry>
```

- Every (version of a) mMojo must be represented by one `mojo`-xml-entry
- The `file`-element represents the relative location from the repository url (as described in the `repositories.xml`).
- The `description`-element is optional, you can put the description from the `product.def` in here.
- Each Mojo contains exactly one Smallworld product (`product`-element).
- The `requires`-element represents the Smallworld product dependencies. Therefore it is optional, if there are no dependencies the element should be omitted.

# Compile Status per repository

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/analysis_workspace/compile.yml?label=analysis_workspace)](https://github.com/krn-sebastiaan/analysis_workspace/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/greeting/compile.yml?label=greeting)](https://github.com/krn-sebastiaan/greeting/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/hello_world/compile.yml?label=hello_world)](https://github.com/krn-sebastiaan/hello_world/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/munit/compile.yml?label=munit)](https://github.com/krn-sebastiaan/munit/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/record_serializers/compile.yml?label=record_serializers)](https://github.com/krn-sebastiaan/record_serializers/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw5-java-object-wrapper/compile.yml?label=sw5-java-object-wrapper)](https://github.com/krn-sebastiaan/sw5-java-object-wrapper/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw5_color_terminal/compile.yml?label=sw5_color_terminal)](https://github.com/krn-sebastiaan/sw5_color_terminal/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw5_openapi_interface_generator/compile.yml?label=sw5_openapi_interface_generator)](https://github.com/krn-sebastiaan/sw5_openapi_interface_generator/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw5_yaml/compile.yml?label=sw5_yaml)](https://github.com/krn-sebastiaan/sw5_yaml/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw_http_server/compile.yml?label=sw_http_server)](https://github.com/krn-sebastiaan/sw_http_server/actions/workflows/compile.yml)

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/krn-sebastiaan/sw_xsd_loader/compile.yml?label=sw_xsd_loader)](https://github.com/krn-sebastiaan/sw_xsd_loader/actions/workflows/compile.yml)
