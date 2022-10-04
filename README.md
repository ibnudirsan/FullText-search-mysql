# FullText Search MySQL

Full-text searching is performed using MATCH() AGAINST() syntax. MATCH() takes a comma-separated list that names the columns to be searched. AGAINST takes a string to search for, and an optional modifier that indicates what type of search to perform. The search string must be a string value that is constant during query evaluation.

```php

<?php

namespace App\Model\articlesBlog;

use Ibnudirsan\FullText\App\Helper\Searchable;

class articlesBlog extends Model
{
   /**
    * Add Searchable at Model
    */
    use Searchable;

   /**
    * Add property $searchable
    */
    protected $searchable = [
        'articleContent'
    ];
}

```
