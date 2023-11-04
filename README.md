# As Relíquias dos Dados

Uma vez que o banco estiver bem estruturado e desenhado, é possível realizar testes, simulando relatórios ou telas que o sistema possa necessitar. A tarefa consiste em criar consultas que levem aos resultados esperados.



-- Criando a VIEW sobre paciente


CREATE  OR REPLACE VIEW `dados_paciente` AS

SELECT 
paciente.paciente_id AS paciente_id, 
paciente.consulta AS consulta_id, 
paciente.telefone AS telefone_id, 
paciente.data_consulta AS data_consulta, 
paciente.valor_consulta AS valor_consulta
 
FROM paciente
INNER JOIN consulta
ON paciente.consulta_id = consulta.consulta_id;

----------------------------------------------------------
    
CREATE  OR REPLACE VIEW `dados_medico` AS

SELECT 

medicos.especialidade_id AS especialidade_id, 
medicos.consulta AS consulta_id, 
medicos.crm AS crm_id, 
medicos.data_consulta AS data_consulta
 
FROM medicos   
    
INNER JOIN medicos
ON medicos.especialidade_id = especialidades.especialidade_id;


-----------------------------------------------------------

-- Selecionando dados da VIEW

SELECT * From dados_pacientes;

select p.nome_paciente, m.nome_medico, i.data_entrada, i.desc_procedimentos, q.id_quarto

From internacao i
INNER JOIN medico m 
ON m.id_medico = i.medico_id
INNER JOIN paciente p
ON p.id_paciente = i.paciente_id
INNER JOIN quarto q
ON q.id_quarto = i.quarto_id
Where q.tipo_id = 3 and m.especialidade_id = 3;


-------------------------------------------------------------

SELECT * From  medico where nome_medico like '%henrique%';





