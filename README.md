# publicrepo

`fww-oauth/` — a one-page relay for the Google sign-in of the funwithworksheets.com admin (Insights).

Google returns to `https://ashishbatraoct.github.io/publicrepo/fww-oauth/?state=…&code=…&iss=https://accounts.google.com…`.
The page keeps only `state` and `code` (or `error`) and forwards them to
`https://funwithworksheets.com/manage/insights/callback/#…`, after a `#`, so the hosting firewall (ModSecurity),
which blocks any parameter value starting with `https://`, never sees Google's `iss` parameter.

The page holds no secrets: the code is useless without the site's client secret and is accepted only together with
the one-time `state` the site created for that sign-in. The target address is fixed in the page.
