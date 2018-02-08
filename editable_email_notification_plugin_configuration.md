## Jenkins Editable Email Notification/Default Content configuration

* **${DEFAULT_SUBJECT}**  
      - This is the default email subject that is configured in Jenkins's system configuration page.  
* **${DEFAULT_CONTENT}**
     - This is the default email content that is configured in Jenkins's system configuration page.
* **${PROJECT_DEFAULT_SUBJECT}** 
   - This is the default email subject for this project. The result of using this token in the advanced configuration is what is in the Default Subject field above. 
   - WARNING: Do not use this token in the Default Subject or Content fields. Doing this has an undefined result.
* **${PROJECT_DEFAULT_CONTENT}**
     - This is the default email content for this project. The result of using this token in the advanced configuration is what is in the Default Content field above.
     -  WARNING: Do not use this token in the Default Subject or Content fields. Doing this has an undefined result.
* **${BUILD_LOG, maxLines, escapeHtml}**  
  - Displays the end of the build log.  
     - _maxLines_ - display at most this many lines of the log.
Defaults to 250.  
     - _escapeHtml_ - If true, HTML is escaped. Defaults to false.  
* **${BUILD_LOG_REGEX,_regex_, _linesBefore_, _linesAfter_, _maxMatches_, _showTruncatedLines_, _substText_, _escapeHtml_, _matchedLineHtmlStyle_}**  
  - Displays lines from the build log that match the regular expression.  
    - _regex_ - Lines that match this regular expression are included. See also java.util.regex.Pattern Defaults to "(?i)\b(error|exception|fatal|fail(ed|ure)|un(defined|resolved))\b".
    - _linesBefore_ - The number of lines to include before the matching line. Lines that overlap with another match or _linesAfter_ are only included once. Defaults to 0.  
     - _linesAfter_ - The number of lines to include after the matching line. Lines that overlap with another match or _linesBefore_ are only included once. Defaults to 0.
     - _maxMatches_ - The maximum number of matches to include. If 0, all matches will be included.Defaults to 0.
     - _showTruncatedLines_ - If true, include ...truncated ### lines... lines. Defaults to true.  
     - _substText_ - If non-null, insert this text into the email rather than the entire line. Defaults to null.  
     - _escapeHtm_ - If true, escape HTML. Defaults to false.  
     - _matchedLineHtmlStyle_ - If non-null, output HTML. matched lines will become <b style="your-style-value">html escaped matched line</b>. Defaults to null.  
* **${BUILD_LOG_EXCERPT, start, end}**  
    - Displays an excerpt from the build log.  
       - _start_ - Regular expression to match the excerpt starting line to be included (excluded). See java.util.regex.Pattern  
       - _end_ - Regular expression to match the excerpt ending line to be included (excluded)  
* **${BUILD_NUMBER}**  
   - Displays the number of the current build.  
* **${BUILD_STATUS}**  
   -  Displays the status of the current build. (failing, success, etc...)  
* **${BUILD_URL}**  
   - Displays the URL to the current build.  
* **${CHANGES, _showPaths_, _showDependencies_, format, _pathFormat_}** 
   - Displays the changes since the last build.  
      - _showDependencies_ - if true, changes to projects this build depends on are shown. Defaults to false.
      - _showPaths_ - if true, the paths modified by a commit are shown.Defaults to false.
      - _format_ - for each commit listed, a string containing %X, where %X is one of %a for    - _author_, %d for date, %m for message, %p for paths, or %r for revision. Not all revision systems support %d and %r. If specified, _showPaths_ is ignored. Defaults to "[%a] %m\n".
     -  _pathFormat_ - a string containing %p to indicate how to print paths. Defaults to "\t%p\n".
* **${CHANGES_SINCE_LAST_SUCCESS, reverse, format, showPaths, changesFormat, pathFormat}**   
  - Displays the changes since the last successful build.
      - _reverse_ - indicates that most recent builds should be at the top. Defaults to false.  
      - _format_ - for each build listed, a string containing %X, where %X is one of %c for changes, or %n for build number. Defaults to "Changes for Build #%n\n%c\n".  
     - _showPaths_, _changesFormat_, _pathFormat_ - defined as _showPaths_, format, and _pathFormat_ from ${CHANGES}, respectively.  
* **${CHANGES_SINCE_LAST_UNSTABLE, reverse, format, _showPaths_, _changesFormat_, _pathFormat_}**  
  - Displays the changes since the last unstable or successful build.  
      - _reverse_ - indicates that most recent builds should be at the top.Defaults to false.  
      - _format_ - for each build listed, a string containing %X, where %X is one of %c for changes, or %n for build number. Defaults to "Changes for Build #%n\n%c\n".  
      - _showPaths_, _changesFormat_, _pathFormat_ - defined as _showPaths_, format, and     
      - _pathFormat_ from ${CHANGES}, respectively.  
* **${ENV, var}**  
   - Displays an environment variable.  
       - _var_ - the name of the environment variable to display. If "", show all.  
Defaults to "".  
* **${FAILED_TESTS, showStack, maxTests}**  
  - Displays failing unit test information, if any tests have failed.  
    - _showStack_ - indicates that most recent builds should be at the top. Defaults to true.  
     - _maxTests_ - display at most this many failing tests.  
No limit is set by default.  
* **${JENKINS_URL}**    
   - Displays the URL to the Jenkins server. (You can change this on the system configuration page.)  
* **${HUDSON_URL}**  
   - deprecated, please use $JENKINS_URL  
* **${PROJECT_NAME}**  
  - Displays the project's name.  
* **${PROJECT_URL}**  
  - Displays a URL to the project's page.  
* **${SVN_REVISION}**  
  - Displays the subversion revision number.  
* **${CAUSE}**  
  - Displays the cause of the build.  
* **${JELLY_SCRIPT, template}**
   - Custom message content generated from a Jelly script template. There are two templates provided: "html" and "text". Custom Jelly templates should be placed in $JENKINS_HOME/email-templates. When using custom templates, the template filename without ".jelly" should be used for the "template" argument.
      - _template_ - the template name.Defaults to "html".  
* **${FILE, path}**  
   - Includes the content of a specified file.  
      - _path_ - The path to the file. Relative to the workspace root.  
* **${TEST_COUNTS, var}**  
  - Displays the number of tests.  
      - _var_ - Defaults to "total".  
      - _total_ - the number of all tests.
      - _fail_ - the number of failed tests.
      - _skip_ - the number of skipped tests.
* **${SCRIPT, script, template, init}**  
  - Custom message content generated from a script using JSR 223. Custom scripts should be placed in $JENKINS_HOME/email-templates. When using custom scripts, the script filename WITH .py/.rb/etc should be used for the "script" argument.  
  - templates and other items may be loaded using the host.readFile(String fileName) function
  - the function will look in the resources for the email-ext plugin first, and then in the $JENKINS_HOME/email-templates directory. No other directories will be searched.  
     - _script_ - the script name. Defaults to "email-ext.groovy".  
     - _template_ - the template filename. Defaults to "groovy-html.template"  
     - _init_ - true to run the language's init script.  Defaults to true  
 
  - Available Script Engines  
      - ECMAScript - 1.8 (js)  
      - Groovy - 1.8.5 (groovy)
