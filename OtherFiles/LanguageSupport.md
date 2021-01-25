Language Support:

To add Language support:
  1. define correct URL Schemes (Example: Server_Uri/MultiIndex/{language})
  2. add parameter to page
  3. add correct Weiterleitung to Startup file (here: MultiStartup.cs)
   there: under public void Configure(...) {
      ...
      app.Use((context, next) => 
        !!!Here!!!
      )
     }
 
Example (for MultiIndex)
Page:
@page {language}

- access value: string lang = RouteData.Values["language"].ToString();

MultiStartup.cs:

if (pathElements.Length == 1)
{
    string defaultRoute = "/MultiIndex";
    string lang = pathElements[0];
    context.Request.Path = new PathString(string.Concat(defaultRoute, '/', lang));
    return next();
}
