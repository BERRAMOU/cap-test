```diff --git a/cmsmap/lib/exploitdbsearch.py b/cmsmap/lib/exploitdbsearch.py
         index 565619b..9a0b01b 100644
         --- a/cmsmap/lib/exploitdbsearch.py
         +++ b/cmsmap/lib/exploitdbsearch.py
         @@ -57,7 +57,7 @@ class ExploitDBSearch:
                          if not initializer.NoExploitdb:
                              if plugin not in self.exclude:
                                  p = subprocess.Popen("grep -ilRE " + self.pluginPath + plugin + "[\&=/] " + self.edbpath + 
         -                            "exploits/php/ | xargs -r grep -ilR " + self.cmstype + 
         +                            "exploits/php/ | xargs -I F grep -ilR " + self.cmstype +
                                      " | cut -d \".\" -f1 | rev | cut -d \"/\" -f1 | rev | sort -u", stdout=subprocess.PIPE, shell=True, universal_newlines=True)
                                  output, error = p.communicate()
                                  ExploitIds = output.splitlines()
         @@ -81,8 +81,8 @@ class ExploitDBSearch:
                      if not initializer.NoExploitdb:
                          if theme not in self.exclude:
                              p = subprocess.Popen("grep -ilR " + theme + " " + self.edbpath + 
         -                        "exploits/php/webapps/ | xargs -r grep -ilR " + self.cmstype + 
         -                        "| xargs -r grep -ilE 'theme|template' | cut -d \".\" -f1 | rev | cut -d \"/\" -f1 | rev | sort -u" , 
         +                        "exploits/php/webapps/ | xargs -I F grep -ilR " + self.cmstype +
         +                        "| xargs -I F grep -ilE 'theme|template' | cut -d \".\" -f1 | rev | cut -d \"/\" -f1 | rev | sort -u" ,
                                  stdout=subprocess.PIPE, shell=True, universal_newlines=True)
                              output , error = p.communicate()
                              ExploitIds = output.splitlines()
       ```
