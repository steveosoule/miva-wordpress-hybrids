# Miva & WordPress Hybrids

## About

Default installs of Miva & WordPress at a site's web root (`/httpdocs/`) can make one CMS accessible and the other one not accessible. We can get them both to work by devoting separate sets of URLs to each CMS.

For example, if we want Miva could show up at `example.com` & the WordPress blog could show up at `example.com/blog/` OR WordPress could show up at `example.com` and Miva could show up at `example.com/store/`. It is not possible for both sites to full cooperate their URL routing without some sort of root-uri-separation.

You'll just need to select one of the methods below and implement the Updates that they describe.

## Methods

There are two file structures in this repo to help demonstrate how Miva & WordPress can be installed at a site's web root:

## [Miva is Primary*](miva-is-primary#miva-is-primary)

## [WordPress is Primary*](wordpress-is-primary#wordpress-is-primary)

_*Note:_ By "Primary" I just mean that going to www.example.com will pull up that CMS's content. The alternate CMS's content will only be visible when using its "sub-directory" in the URL.