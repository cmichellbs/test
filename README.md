SELECT 
    MAX(t.lead_no) AS lead_no,
    t.Empresa,
    t.RazaoSocial,
    t.CNPJ_CPF,
    t.Cargo,
    t.Setor,
    MAX(t.Responsavel) AS 'Responsavel',
    t.PreVenda,
    t.PerfildaOportunidade,
    MAX(t.FonteLead) AS 'FonteLead',
    MAX(t.SubOrigemLead) AS 'SubOrigemLead',
    MAX(t.Pontuacao) AS 'Pontuacao',
    MAX(t.Parceiro) AS 'Parceiro',
    MAX(t.DataHoraCriacao) AS 'DataHoraCriacao',
    MAX(t.TemperaturaLead) AS 'TemperaturaLead',
    MAX(t.CódigoCNAEPrincipalCNPJ) AS 'CódigoCNAEPrincipalCNPJ',
    MAX(t.CapitalSocialCNPJ) AS 'CapitalSocialCNPJ',
    t.CNPJExactSales,
    MAX(t.DescriçãoCNAEPrincipalCNPJ) AS 'DescriçãoCNAEPrincipalCNPJ',
    t.Eh_LM,
    MAX(t.Eh_CORPouPME) AS 'Eh_CORPouPME',
    t.UsaSoftwareDeTratamento,
    t.LMComoConheceuAhgora,
    t.LMPorqueEstaoBuscandoSolucao,
    t.TemColaboradoresExternos,
    t.QuantosColaboradoresExternos,
    t.QuantasU0nidades,
    MAX(t.QuantidadeDeFuncionariosTotal) AS 'QuantidadeDeFuncionariosTotal',
    t.QuandoVoccGostariaDeTeroProjetoRodando,
    t.EhLMAcesso,
    t.LMQuantasUnidadesAEmpresaTem,
    t.LMPorqueEstaoBuscandoUmaSolucaoAcesso,
    t.LMQualaquantidadeDeFuncionariosTotal,
    t.LMEmQualLocalFicaraoControleDeAcesso,
    t.LMQuantosEquipamentosVocePrecisa,
    t.QualaCategoriaDoLead,
    t.QualaQuantidadeDeFuncionariosTotal,
    t.QuantasEmpresasAtendem,
    t.QuandoVoceGostariaDeTeroProjetoRodando_C,
    t.DprDoLead,
    t.CEP,
    t.Cidade,
    t.Pais,
    t.Estado,
    t.PrimeiroEventoConversao,
    MAX(t.UltimoEventoConversao) AS UltimoEventoConversao,
    t.QuizASuaEmpresaTemMaisDeumCNPJ,
    MAX(t.VendedorResponsavel) AS VendedorResponsavel,
    MAX(t.DataAgendamento) AS 'DataAgendamento',
    t.Email,
    t.EmailAlternativo,
    t.TemAcessoIntegradoAoPonto,
    MAX(t.leads) AS 'leads',
    MAX(t.agendados) AS 'agendados',
    MAX(t.oportunidade) AS 'oportunidade',
    biahgora.dimusuarios.Nome,
    MAX(t.Cadencia) AS Cadencia,
    t.DatamodificacaoLead AS 'DataInteração',
    t.idPrimeiraCotacao,
    MAX(t.cotacao) AS 'cotacao',
    MAX(t.saas) AS saas,
    MAX(t.servico) AS servico,
    MAX(t.produtos) AS produtos,
    MAX(t.locacao) AS locacao,
    MAX(t.DataCotacao) AS 'DataCotacao',
    t.pdv_id,
    MAX(t.PDV) AS 'PDV',
    MAX(t.dataPedido) AS 'dataPedido',
    MAX(t.MQL) AS 'MQL',
    MAX(t.DataOPT) AS 'DataOPT',
    MAX(t.Devolvido) AS 'Devolvido',
    MAX(t.cod_opt) AS 'cod_opt',
    MAX(t.tipoCliente) AS tipoCliente,
    IF(	(MAX(t.PDV_m) = 1)
		OR (MAX(t.cotacao_m) = 1)
		OR (MAX(t.oportunidade_m) = 1)
		OR (MAX(t.agendados) = 1)
		  ,1, 0) AS 'origem_mkt',
		
    MAX(t.oportunidade_m) AS oportunidade_m,
    MAX(t.cotacao_m) AS cotacao_m,
    MAX(t.PDV_m) AS PDV_m,
    IF((t.dataPedido IS NOT NULL)
            AND (t.DataHoraCriacao IS NOT NULL),
        DATEDIFF(t.dataPedido, t.DataHoraCriacao),
        NULL) AS 'lea_pdv',
    IF((t.DataAgendamento IS NOT NULL)
            AND (t.DataHoraCriacao IS NOT NULL),
        DATEDIFF(t.DataAgendamento, t.DataHoraCriacao),
        NULL) AS 'lea_age',
    IF((t.DataOPT IS NOT NULL)
            AND (t.DataHoraCriacao IS NOT NULL),
        DATEDIFF(t.DataOPT, t.DataHoraCriacao),
        NULL) AS 'lea_opt',
    IF((t.DataCotacao IS NOT NULL)
            AND (t.DataHoraCriacao IS NOT NULL),
        DATEDIFF(t.DataCotacao, t.DataHoraCriacao),
        NULL) AS 'lea_cot',
    IF((t.DataAgendamento IS NOT NULL)
            AND (t.DataOPT IS NOT NULL),
        DATEDIFF(t.DataOPT, t.DataAgendamento),
        NULL) AS 'age_opt',
    IF((t.DataAgendamento IS NOT NULL)
            AND (t.dataPedido IS NOT NULL),
        DATEDIFF(t.dataPedido, t.DataAgendamento),
        NULL) AS 'age_pdv',
    IF((t.dataPedido IS NOT NULL)
            AND (t.DataOPT IS NOT NULL),
        DATEDIFF(t.dataPedido, t.DataOPT),
        NULL) AS 'opt_pdv',
    IF((t.DataAgendamento IS NOT NULL)
            AND (t.DataCotacao IS NOT NULL),
        DATEDIFF(t.DataCotacao, t.DataAgendamento),
        NULL) AS 'age_cot',
    IF((t.DataCotacao IS NOT NULL)
            AND (t.DataOPT IS NOT NULL),
        DATEDIFF(t.DataCotacao, t.DataOPT),
        NULL) AS 'opt_cot',
    IF((t.DataCotacao IS NOT NULL)
            AND (t.dataPedido IS NOT NULL),
        DATEDIFF(t.dataPedido, t.DataCotacao),
        NULL) AS 'cot_pdv',
    MAX(t.idpedido) AS 'idpedido',
    MAX(t.cod_pdv) AS 'cod_pdv',
    MAX(t.observacao) AS 'observacao',
    if(MAX(t.observacao) like "%Fluxo Automatizado%","Sim","Não") as Venda_Automatizada
FROM
    (SELECT 
        biahgora.dimleads.CadanciaProspeccao AS 'Cadencia',
            biahgora.dimleads.lead_no,
            biahgora.dimleads.Empresa,
            biahgora.dimleads.RazaoSocial,
            biahgora.dimleads.CNPJ_CPF,
            biahgora.dimleads.Cargo,
            biahgora.dimleads.Setor,
            IFNULL(biahgora.dimleads.VendedorResponsavel, biahgora.dimleads.Responsavel) AS 'Responsavel',
            biahgora.dimleads.PreVenda,
            biahgora.dimleads.PerfildaOportunidade,
            biahgora.dimleads.FonteLead,
            biahgora.dimleads.SubOrigemLead,
            biahgora.dimleads.Pontuacao,
            biahgora.dimleads.Parceiro,
            biahgora.dimleads.DataHoraCriacao,
            biahgora.dimleads.TemperaturaLead,
            biahgora.dimleads.CódigoCNAEPrincipalCNPJ,
            biahgora.dimleads.CapitalSocialCNPJ,
            biahgora.dimleads.CNPJExactSales,
            biahgora.dimleads.DescriçãoCNAEPrincipalCNPJ,
            biahgora.dimleads.Eh_LM,
            biahgora.dimleads.Eh_CORPouPME,
            biahgora.dimleads.UsaSoftwareDeTratamento,
            biahgora.dimleads.LMComoConheceuAhgora,
            biahgora.dimleads.LMPorqueEstaoBuscandoSolucao,
            biahgora.dimleads.TemColaboradoresExternos,
            biahgora.dimleads.QuantosColaboradoresExternos,
            biahgora.dimleads.QuantasU0nidades,
            biahgora.dimleads.QuantidadeDeFuncionariosTotal,
            biahgora.dimleads.QuandoVoccGostariaDeTeroProjetoRodando,
            biahgora.dimleads.EhLMAcesso,
            biahgora.dimleads.LMQuantasUnidadesAEmpresaTem,
            biahgora.dimleads.LMPorqueEstaoBuscandoUmaSolucaoAcesso,
            biahgora.dimleads.LMQualaquantidadeDeFuncionariosTotal,
            biahgora.dimleads.LMEmQualLocalFicaraoControleDeAcesso,
            biahgora.dimleads.LMQuantosEquipamentosVocePrecisa,
            biahgora.dimleads.QualaCategoriaDoLead,
            biahgora.dimleads.QualaQuantidadeDeFuncionariosTotal,
            biahgora.dimleads.QuantasEmpresasAtendem,
            biahgora.dimleads.QuandoVoceGostariaDeTeroProjetoRodando_C,
            biahgora.dimleads.DprDoLead,
            biahgora.dimleads.CEP,
            biahgora.dimleads.Cidade,
            biahgora.dimleads.Pais,
            biahgora.dimleads.Estado,
            biahgora.dimleads.PrimeiroEventoConversao,
            biahgora.dimleads.UltimoEventoConversao,
            biahgora.dimleads.QuizASuaEmpresaTemMaisDeumCNPJ,
            biahgora.dimleads.VendedorResponsavel,
            biahgora.dimleads.DataAgendamento,
            biahgora.dimleads.Email,
            biahgora.dimleads.EmailAlternativo,
            biahgora.dimleads.TemAcessoIntegradoAoPonto,
            1 AS 'leads',
            IF((((biahgora.dimleads.CadanciaProspeccao LIKE 'AGENDADOS'
                OR biahgora.dimleads.CadanciaProspeccao LIKE 'REAGENDAMENTO'
                OR biahgora.dimleads.CadanciaProspeccao LIKE 'REUNIÃO NÃO OCORRIDA'
                OR biahgora.dimleads.CadanciaProspeccao LIKE 'REUNIÃO OCORRIDA')
                AND (biahgora.dimleads.PreVenda IS NOT NULL
                AND biahgora.dimleads.PreVenda NOT LIKE '%aplica%'
                AND biahgora.dimleads.PreVenda NOT LIKE ''))
                OR (biahgora.dimleads.CadanciaProspeccao LIKE 'DESCARTADO'
                AND biahgora.dimleads.FeedbackReuniao = 1)
                OR (biahgora.dimleads.CNPJExactSales IS NOT NULL
                AND biahgora.dimleads.CadanciaProspeccao IS NULL)
                OR (biahgora.dimleads.DataAgendamento IS NOT NULL
                AND (biahgora.dimleads.PreVenda IS NOT NULL
                AND biahgora.dimleads.PreVenda NOT LIKE '%aplica%'
                AND biahgora.dimleads.PreVenda NOT LIKE '')))
                AND (biahgora.dimleads.FonteLead NOT LIKE '%SUCESSO%'
                AND biahgora.dimleads.FonteLead NOT LIKE '%Base%'), 1, 0) AS 'agendados',
            0 AS 'oportunidade',
            biahgora.dimleads.DatamodificacaoLead,
            NULL AS 'idPrimeiraCotacao',
            NULL AS 'saas',
            NULL AS 'produtos',
            NULL AS 'servico',
            NULL AS 'locacao',
            0 AS 'cotacao',
            NULL AS 'DataCotacao',
            NULL AS 'pdv_id',
            0 AS 'PDV',
            NULL AS 'dataPedido',
            IF(biahgora.dimleads.UltimoEventoConversao IS NULL
                AND (biahgora.dimleads.FonteLead NOT LIKE 'Indicação'
                OR biahgora.dimleads.FonteLead NOT LIKE 'Inbound'), 0, 1) AS 'MQL',
            biahgora.dimleads.DataHoraCriacao AS 'DataOPT',
            biahgora.dimleads.DesejaDevolverOLeadParaOsDR AS 'Devolvido',
            biahgora.dimleads.lead_no AS cod_opt,
            IF((biahgora.dimleads.FonteLead LIKE 'SUCESSO_DO_CLIENTE')
                OR (biahgora.dimleads.FonteLead LIKE 'Cliente da Base'), 1, 0) AS 'tipoCliente',
            0 AS 'oportunidade_m',
            0 AS 'cotacao_m',
            0 AS 'PDV_m',
            NULL AS idpedido,
            NULL AS cod_pdv,
            null as 'observacao'
    FROM
        biahgora.dimleads
    WHERE
        biahgora.dimleads.lead_no NOT IN (SELECT 
                biahgora.fatooportunidade.CodigoLead
            FROM
                biahgora.fatooportunidade
            WHERE
                biahgora.fatooportunidade.CodigoLead IS NOT NULL) UNION (SELECT 
        'REUNIÃO OCORRIDA' AS 'Cadencia',
            biahgora.fatooportunidade.potential_no,
            biahgora.dimorganizacoes.nomeOrganizacao,
            biahgora.dimorganizacoes.razaoSocial,
            biahgora.dimorganizacoes.CPFCNPJ,
            c.Cargo,
            c.Setor,
            biahgora.fatooportunidade.idUsuarioGluoVendedor,
            biahgora.fatooportunidade.PreVenda,
            biahgora.fatooportunidade.PerfilDaOportunidade,
            biahgora.fatooportunidade.fonteLead,
            biahgora.fatooportunidade.SubOrigemLead,
            biahgora.fatooportunidade.Pontuacao,
            CONCAT('11x', biahgora.fatooportunidade.ContabilidadeCliente),
            biahgora.fatooportunidade.DataCriacaoLead AS 'DataCriacaoLead',
            biahgora.fatooportunidade.TemperaturaLead,
            biahgora.dimorganizacoes.CodigoCNAEPrincipalCNPJ,
            biahgora.dimorganizacoes.CapitalSocialCNPJ,
            biahgora.dimorganizacoes.CPFCNPJ,
            biahgora.dimorganizacoes.DescricaoCNAEPrincipalCNPJ,
            biahgora.fatooportunidade.LevantadaDeMao,
            biahgora.fatooportunidade.EhCORP_ou_PME,
            biahgora.fatooportunidade.UsaAlgumSistemaParaTratarOPonto,
            biahgora.fatooportunidade.LMComoConheceuAAhgora,
            biahgora.fatooportunidade.LMPorqueEstaoBuscandoSolucao,
            biahgora.fatooportunidade.TemColaboradoresExtermos,
            biahgora.fatooportunidade.Quantos,
            biahgora.fatooportunidade.QuantasUnidadesFiliais,
            biahgora.fatooportunidade.QuantidadeDeFuncionariosTotal,
            biahgora.fatooportunidade.QuandoVoceGostariaDeTerOProjetoRodando,
            biahgora.fatooportunidade.LevantadaDeMaoAcesso,
            biahgora.fatooportunidade.LMQuantasUnidadesAEmpresaTem,
            biahgora.fatooportunidade.LMPorqueEstaoBuscandoUmaSolucaoAcesso,
            biahgora.fatooportunidade.LMQualAQuantidadeDeFuncionariosTotal,
            biahgora.fatooportunidade.LMEmQualLocalFicaraOControleDeAcesso,
            biahgora.fatooportunidade.LMQuantosEquipamentosVocePrecisa,
            biahgora.fatooportunidade.QualACategoriaDoLead,
            biahgora.fatooportunidade.QualAQuantidadeFuncionáriosTotal,
            biahgora.fatooportunidade.QuantasEmpresasAtendem,
            biahgora.fatooportunidade.QuandoVoceGostariaDeTerOProjetoRodando_1,
            biahgora.fatooportunidade.DorDoLeadSDR,
            biahgora.dimorganizacoes.CEPFaturamento,
            biahgora.dimorganizacoes.CidadeFaturamento,
            biahgora.dimorganizacoes.pais,
            biahgora.dimorganizacoes.UFFaturamento,
            biahgora.fatooportunidade.PrimeiroEventoConvercao,
            biahgora.fatooportunidade.UltimoEventoConversao,
            biahgora.fatooportunidade.QuizASuaEmpresaTemMaisDeUmCNPJ,
            biahgora.fatooportunidade.idUsuarioGluoVendedor,
            IFNULL(biahgora.fatooportunidade.DataUltimoAgendamento, biahgora.fatooportunidade.dataCriacao) AS 'DataAgendamento',
            c.Email,
            c.EmailAlternativo,
            biahgora.fatooportunidade.TemAcessoIntegradoAoPonto,
            IF(biahgora.fatooportunidade.ConvertidoAPartirDoLEAD = 1, 1, 0) AS 'leads',
            IF((biahgora.fatooportunidade.ConvertidoAPartirDoLEAD = 1 
                 OR ((biahgora.fatooportunidade.PreVenda NOT LIKE ''
                AND biahgora.fatooportunidade.PreVenda NOT LIKE '%aplica%'
                AND biahgora.fatooportunidade.PreVenda IS NOT NULL)
                AND (biahgora.fatooportunidade.fonteLead NOT LIKE '%SUCESSO%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Base%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Vendedor%'))), 1, 0) AS 'agendados',
            IF((biahgora.fatooportunidade.potential_no IS NOT NULL), 1, 0) AS 'oportunidade',
            biahgora.fatooportunidade.DataPrimeiraInteracao,
            biahgora.fatooportunidade.idPrimeiraCotacao,
            biahgora.fatocotacoes.valor_SaaS 'saas',
            biahgora.fatocotacoes.valor_Produtos 'produtos',
            biahgora.fatocotacoes.valor_Servicos_Tecnicos 'servico',
            biahgora.fatocotacoes.valor_Locacao 'locacao',
            IF(biahgora.fatooportunidade.idPrimeiraCotacao IS NOT NULL, 1, 0) AS 'cotacao',
            biahgora.fatocotacoes.dataCriacao AS 'DataCotacao',
            biahgora.fatooportunidade.idPedidoGluo AS 'pdv_id',
            IF(biahgora.fatooportunidade.idPedidoGluo IS NOT NULL, 1, 0) AS 'PDV',
            biahgora.fatopedidodevendas.dataPedido,
            IF(biahgora.fatooportunidade.UltimoEventoConversao IS NULL
                AND (biahgora.fatooportunidade.fonteLead NOT LIKE 'Indicação'
                OR biahgora.fatooportunidade.fonteLead NOT LIKE 'Inbound'), 0, 1) AS 'MQL',
            biahgora.fatooportunidade.dataCriacao AS 'DataOPT',
            0 AS 'Devolvido',
            biahgora.fatooportunidade.potential_no AS cod_opt,
            biahgora.dimoportunidade.tipoCliente,
            IF((biahgora.fatooportunidade.ConvertidoAPartirDoLEAD = 1
                and ((biahgora.fatooportunidade.PreVenda NOT LIKE ''
                AND biahgora.fatooportunidade.PreVenda NOT LIKE '%aplica'
                AND biahgora.fatooportunidade.PreVenda IS NOT NULL))
                AND (biahgora.fatooportunidade.fonteLead NOT LIKE '%SUCESSO%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Base%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Vendedor%')), 1, 0) AS 'oportunidade_m',
            IF((biahgora.fatooportunidade.ConvertidoAPartirDoLEAD = 1
                and ((biahgora.fatooportunidade.PreVenda NOT LIKE ''
                AND biahgora.fatooportunidade.PreVenda NOT LIKE '%aplica'
                AND biahgora.fatooportunidade.PreVenda IS NOT NULL))
                AND (biahgora.fatooportunidade.fonteLead NOT LIKE '%SUCESSO%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Base%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Vendedor%'))
                AND biahgora.fatooportunidade.idPrimeiraCotacao IS NOT NULL, 1, 0) AS 'cotacao_m',
            IF((biahgora.fatooportunidade.ConvertidoAPartirDoLEAD = 1
                and ((biahgora.fatooportunidade.PreVenda NOT LIKE ''
                AND biahgora.fatooportunidade.PreVenda NOT LIKE '%aplica'
                AND biahgora.fatooportunidade.PreVenda IS NOT NULL))
                AND (biahgora.fatooportunidade.fonteLead NOT LIKE '%SUCESSO%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Base%'
                AND biahgora.fatooportunidade.fonteLead NOT LIKE '%Vendedor%'))
                AND biahgora.fatooportunidade.idPedidoGluo IS NOT NULL, 1, 0) AS 'PDV_m',
            biahgora.fatooportunidade.idPedidoGluo AS idpedido,
            biahgora.fatopedidodevendas.pdv AS cod_pdv,
            biahgora.fatooportunidade.F_ObservacoesParaOPreVendedor as 'observacao'
    FROM
        biahgora.fatooportunidade
    LEFT JOIN dimorganizacoes ON biahgora.fatooportunidade.idOrganizacaoGluo = biahgora.dimorganizacoes.idOrganizacaoGluo
    LEFT JOIN biahgora.fatocotacoes ON biahgora.fatocotacoes.idCotacaoGluo = biahgora.fatooportunidade.idPrimeiraCotacao
    LEFT JOIN biahgora.dimoportunidade ON biahgora.dimoportunidade.sk_oportunidade = biahgora.fatooportunidade.sk_oportunidade
    LEFT JOIN biahgora.fatopedidodevendas ON biahgora.fatooportunidade.id = biahgora.fatopedidodevendas.idOportunidade
    LEFT JOIN (SELECT 
        biahgora.dimcontatos.Cargo,
            biahgora.dimcontatos.Setor,
            biahgora.dimcontatos.Email,
            biahgora.dimcontatos.EmailAlternativo,
            biahgora.dimcontatos.idOrganizacao
    FROM
        biahgora.dimcontatos
    GROUP BY biahgora.dimcontatos.idOrganizacao) c ON c.idOrganizacao = biahgora.dimorganizacoes.idOrganizacaoGluo)) t
        LEFT JOIN
    biahgora.dimusuarios ON t.Responsavel = biahgora.dimusuarios.idUsuarioGluo
GROUP BY t.lead_no
