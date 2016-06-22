---
layout: post
title: Hydra Sandbox Setup and Configuration Notes
tags: [hydra, sandbox, development]
authors:
    - yang_li
---

This is a note for developers who are attempting to setup Hydra project on a Mac in the Emory LITS setting. It includes some of the general steps introduced in the Hydra framework GitHub tutorial together with some documentations summarized from the installation process we did ourselves.  

```shell
ssh hydrabox.library.emory.edu
```

use the NetID to login which should be the `abc1234`  

There are two important directories:

```shell
/etc/httpd/ # apache
/var/www/ # packages
```

A few other important endpoints are:

```shell
http://goldenseal.library.emory.edu/ # Emory Golden Seal
http://curationconcerns.library.emory.edu/ # Emory Curation Concerns
```

Fedora 4 endpoint:

```shell
https://hydrabox.library.emory.edu:8443/fcrepo/rest/
# Tip: Get credentials from LITS Dev Team members.
```

Solr endpoint:

```shell
https://hydrabox.library.emory.edu:9193/solr/#/
```

GitHub repo wise let's visit emory-libraries

Checkout a few repos here:

```shell
git clone git@github.com:emory-libraries/EmoryCurationConcerns.git
bundle install
```

If you run into a MySQL error it’s more than likely that you don’t have MySQL setup or running. Try:

```shell
brew install mysql
```

Get the private files from someone:

```shell
config/database.yml
config/fedora.yml
config/solr.yml
config/hydra-ldap.yml
config/redis.yml
config/blacklight.yml
config/secret.yml
```

Can point local solr to the playground/sandbox that is:

```shell
https://hydrabox.library.emory.edu:9193/solr/blacklight-core
```  

Another one that we can look at is the CurationConcerns from the ProjectHydra:

```shell
https://github.com/projecthydra-labs/curation_concerns
```   

Install dependencies for curationconcerns:

```shell
https://github.com/projecthydra/hydra-derivatives#dependencies
```  

EmoryCurationConcerns - our version
* didn’t clone off the projecthydra   
* it’s a customized project - generic hydra head + curation and concern gem = we have CC for Hydra
reason: we’d like to customize the authorization system etc.

Get Java from Oracle if you don’t have one installed yet:

```shell
java -version # to verify your java sdk version
```  

A few dependencies:

```shell
brew install fits  
brew install ffmpeg  
brew install imagemagick  
```

Restart MySQL:

```shell
brew services start mysql
```

database.yml:
get the `database.yml` from the server
create your own database and make sure the db matches up with the db.yml

You could potentially run into this error:

```shell
/Users/yli60/Documents/emory/projects/EmoryCurationConcerns/config/initializers/curation_concerns.rb:2:in block in <top (required)>: undefined method fits_to_desc_mapping= for #<CurationConcerns::Configuration:0x007fa460b9bca0> (NoMethodError)
```

Don’t have curation and concerns yet:

```shell
rails generate curation_concerns:install
```  

uncomment out `devise.rb` and `blacklight.rb` in the `initializer.rb`

And install redis with:

```shell
brew install redis
```

Add blacklight gem to the gemfile and bundle    
then run the generate on the hydra:head:

```shell
rails g hydra:head -f
```

```shell
last:  
migrate:  
rake db:migrate   
```

If it prompts you with errors such as curation_concerns not found, we can try reinstalling the cc:

```shell
gem install curation__concerns  
rails generate curation__concerns:install  
```

A few other good ones shared by the team:  

[Solr in 5 Minutes](https://www.youtube.com/watch?v=ClhrrPzJWmI)

[Fedora Repository is not the Linux distribution](https://www.youtube.com/watch?v=U9jaFM0Q2h0)

this may also be of interest - more about the "onion skin" layers of Hydra functionality:   [Dive into Hydra Works](https://github.com/projecthydra-labs/hydra-works/wiki/Dive-into-Hydra-Works)

[A More Worthwhile Sufia Now with PCDM](http://www.slideshare.net/jpstroop/a-more-worthwhile-sufia-now-with-pcdm)

[Hydra Technical Deepdive](http://www.slideshare.net/DuraSpace/hydra-technical-deepdive)
