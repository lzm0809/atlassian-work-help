## 查询项目与方案之间的关系
```mysql
SELECT
	p.id AS project_id ,
	p.pname AS project_name ,
	p.lead AS project_lead ,
	ws. NAME AS field_scheme,
	iss. NAME AS issuetype_s_scheme, 
	works. NAME AS workflow_scheme,
	issuetype_s.configname  AS issuetype_scheme 
-- 	wse.workflow AS workflow_scheme_associated_workflow ,
-- 	jw.descriptor AS workflow_descriptor
FROM
	project p
left join nodeassociation cn on cn.SOURCE_NODE_ID = p.id and cn.SINK_NODE_ENTITY='ProjectCategory' 
LEFT JOIN nodeassociation na ON na.source_node_id = p.id
AND na.sink_node_entity = 'FieldLayoutScheme'
LEFT JOIN fieldlayoutscheme ws ON ws.id = na.sink_node_id
-- isstypescreen
LEFT JOIN nodeassociation iss_n ON iss_n.source_node_id = p.id
AND iss_n.sink_node_entity = 'IssueTypeScreenScheme'
LEFT JOIN issuetypescreenscheme iss ON iss.id = iss_n.sink_node_id
-- workflow
LEFT JOIN nodeassociation work_n ON work_n.source_node_id = p.id
AND work_n.sink_node_entity = 'WorkflowScheme'
LEFT JOIN workflowscheme works ON works.id = work_n.sink_node_id

-- issuetype
LEFT JOIN configurationcontext issuetype ON issuetype.project = p.id
AND issuetype.customfield = 'issuetype'
LEFT JOIN fieldconfigscheme issuetype_s ON issuetype_s.id = issuetype.FIELDCONFIGSCHEME

-- LEFT OUTER JOIN workflowschemeentity wse ON wse.scheme = ws.id
-- LEFT OUTER JOIN jiraworkflows jw ON jw.workflowname = wse.workflow
#WHERE p.pname='EDU'
WHERE cn.SINK_NODE_ID = <category_id>
```
