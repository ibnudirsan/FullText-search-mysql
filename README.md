# FullText Search MySQL

Full-text searching is performed using MATCH() AGAINST() syntax. MATCH() takes a comma-separated list that names the columns to be searched. AGAINST takes a string to search for, and an optional modifier that indicates what type of search to perform. The search string must be a string value that is constant during query evaluation.

```php

<?php

namespace App\Model\articlesBlog;

use Ibnudirsan\FullText\App\Helper\Searchable;

/*
|--------------------------------------------------------------------------
| Rumah Dev
| Backend Developer : ibudirsan
| Email             : ibnudirsan@gmail.com
| Copyright © RumahDev 2022
|--------------------------------------------------------------------------
*/

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

```php

<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
use Ibnudirsan\FullText\App\Helper\Searchable;

/*
|--------------------------------------------------------------------------
| Rumah Dev
| Backend Developer : ibudirsan
| Email             : ibnudirsan@gmail.com
| Copyright © RumahDev 2022
|--------------------------------------------------------------------------
*/

class PostBlogsController extends Controller
{
    use Searchable;
    
    public function search($search) {
        $result = articlesBlog::select('id', 'TitleArticle', 'slugArticle', 'Excerpt', 'articleContent')
                                ->search($search)
                                ->get();            
        return $result;
    }
}
```
