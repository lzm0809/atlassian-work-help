## 查询项目与方案之间的关系
```mysql
SELECT
	p.id AS project_id ,
	p.pname AS project_name ,
	p.lead AS project_lead ,
	ws. NAME AS project_associated_workflow_scheme 
-- 	wse.workflow AS workflow_scheme_associated_workflow ,
-- 	jw.descriptor AS workflow_descriptor
FROM
	project p
LEFT JOIN nodeassociation na ON na.source_node_id = p.id
AND na.sink_node_entity = 'FieldLayoutScheme'
LEFT JOIN fieldlayoutscheme ws ON ws.id = na.sink_node_id
-- LEFT OUTER JOIN workflowschemeentity wse ON wse.scheme = ws.id
-- LEFT OUTER JOIN jiraworkflows jw ON jw.workflowname = wse.workflow
WHERE p.pname='<projectname>'
```
