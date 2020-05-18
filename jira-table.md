|Table|Desc|
|:-|:-|
|cwd_user|用户主表|
|cwd_user_attributes|用户属性表，登陆次数、最后登陆时间、登陆失败次数等login.lastLoginMillis = 最后登录时间（秒）|
|cwd_group|用户组|
|jiraissue|issue主表|
|customfield|自定义字段|
|customfieldvalue|自定义字段的值|
|nodeassociation|存储关联关系，包含project - project_category、project对应的schema信息|
|nodeassociation|项目与方案之间的关联关系，注：不包括问题类型页面方案|
|configurationcontext|项目与问题类型方案之间的关联关系|
|fieldconfigscheme|问题类型页面方案|
|fieldconfigschemeissuetype|问题类型方案与问题类型的关联关系|