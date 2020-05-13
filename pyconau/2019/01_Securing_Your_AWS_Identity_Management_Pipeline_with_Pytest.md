# Securing your AWS Identity Management pipeline with PyTest
## Sean Johnson

* Terraform
    * Terraform Validate
    * Nothing to really ensure IAM standards are enforced.
* Getting IAM definitions
    * Scraped (using BeautifulSoup) because AWS
* Pytest
    * Pytest can test anything!
    * Anyone can write these tests!
    * Plugin
        * Define a setuptools entry point for `pytest11`
        * Define your filter in `plugin.py`
        * Yield subclassed `pytest` item - overload of builtin `pytest.Item`.
* This plugin
    * PyHCL
    * Publish your module
    * Install your module
    * Run pytest!
