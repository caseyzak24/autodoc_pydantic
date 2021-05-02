# Changelog

## v1.1.1 - 2021-04-26

This is a minor release with focus on refactoring and doc strings.

### Internal

- Several minor readability refactorings.

### Documentation

- Add changelog and `myst_parser` for parsing markdown files.

### Project

- Add animated example to showcase difference between standard sphinx autodoc
  and pydantic autodoc.
- Add project logo.
- Add changelog.


## v1.1.0 - 2021-04-24

This is small feature release enabling `autodoc_pydantic` to handle non JSON 
serializable fields properly.

### Internal

- Replace inspection methods that use models JSON schema with methods that
  directly access relevant pydantic object attributes.
- Intercept non JSON serializable fields and overwrite types and default values
  indicating serialization error.
  
### Documentation

- Add explicit note about how non JSON serializable fields are handled for 
  `model-show-json` and `settings-show-json`.

## v1.0.0 - 2021-04-23

This is a major release providing API stability with main focus on extensive 
tests and documentation.

### Added

- Add custom css for `autodoc_pydantic` extension.

### Internal

- Add `PydanticAutoDirective` as composite class to mainly manage 
  option/configuration management for directives.
- Add `PydanticAutoDoc` as composite class to mainly 
  manage option/configuration management for autodocumenters.
- Unify directive options and global configuration settings via composite classes.
- Add option validators `option_members`, `option_one_of_factory`, 
  `option_default_true`, `option_list_like`.

### Documentation

- Add extensions to automate documentation generation:
  - `ConfigurationToc` to generate options/conf toc mappings from usage to 
    configuration section
  - `TabDocDirective` to generate rendered examples in configuration section
  - `AutoCodeBlock` to generate code block from object path
  
- Add user guide:
  - Installation
  - Usage
  - Configuration
  - Examples

- Add developer guide:
  - Setting up development environment
  - Running tests
  - Building docs
  
- Add `.readthedocs.yaml`.

### Testing

- Add test python package with code examples for test execution (same structure
  as sphinx tests).
- Add fixture `test_app` to instantiate test app with settable configuration
  settings.
- Add fixture `autodocument` to handle restructured text generation tests 
  (autodocumenter tests).
- Add fixture `parse_rst` to handle node generation tests from restructured
  text (directive tests).
- Add autodoc/directive tests for all available configuration settings
- Include sourcery in CI pipeline.

### Packaging

- Modify package dependencies to `sphinx >=3.4` and `pydantic >= 1.5`.

## v0.1.1 - 2021-04-04

This release adds the sphinx documentation skeleton.

### Documentation

- Add initial sphinx documentation.

## v0.1.0 - 2021-03-30

This is the initial of autodoc_pydantic.

### Added

- Autodocumenter `PydanticModelDocumenter` with configurations:
  - `model_show_json`
  - `model_show_config_member`
  - `model_show_config_summary`
  - `model_show_validator_members`
  - `model_show_validator_summary`
  - `model_hide_paramlist`
  - `model_undoc_members`
  - `model_members`
  - `model_member_order`
  - `model_signature_prefix`
  
- Autodocumenter `PydanticSettingsDocumenter` with configurations:
  - `settings_show_json`
  - `settings_show_config_member`
  - `settings_show_config_summary`
  - `settings_show_validator_members`
  - `settings_show_validator_summary`
  - `settings_hide_paramlist`
  - `settings_undoc_members`
  - `settings_members`
  - `settings_member_order`
  - `settings_signature_prefix`
  
- Autodocumenter `PydanticFieldDocumenter` with configurations:
  - `field_list_validators`
  - `field_doc_policy`
  - `field_show_constraints`
  - `field_show_alias`
  - `field_show_default`
  - `field_signature_prefix`
  
- Autodocumenter `PydanticValidatorDocumenter` with configurations:
  - `validator_signature_prefix`
  - `validator_replace_signature`
  - `validator_list_fields`
  
- Autodocumenter `PydanticConfigClassDocumenter` with configurations:
  - `config_signature_prefix`
  - `config_members`
  
- Directives `PydanticModel`, `PydanticSettings`, `PydanticField`, `PydanticValidator`, `PydanticConfigClass` 

### Internal

- Add `inspection` along with `ModelWrapper` module providing functionality 
  to inspect pydantic objects to retrieve relevant informations for documentation.

### Testing

- Add end to end tests for autodocumenters and directives.
- Setup github actions for CI.
- Add codacy integration.
- Add code coverage.

### Packaging

- Use poetry for package management.
- Add `pyproject.toml`.
- Add github action to upload to PyPI upon version tags on main branch.