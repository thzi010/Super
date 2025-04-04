-- !!! ATENÇÃO: Este script assume a existência de funções específicas do jogo que provavelmente NÃO existem.
-- !!! A funcionalidade real depende inteiramente de como o jogo expõe (ou não) seus dados internos para scripts.

function adicionarMinhasGemas(quantidade)
  if jogo and jogo.temGemas and jogo.temGemas() then
    local gemasAtuais = 0
    if jogo.getGemasAtuais then
      gemasAtuais = jogo.getGemasAtuais()
    end

    local novasGemas = gemasAtuais + quantidade

    if jogo.setGemas then
      jogo.setGemas(novasGemas)
      -- Se a função 'jogo.setGemas' realmente salvar os dados do jogo,
      -- as gemas serão persistentes até serem gastas.
    else
      -- Erro silencioso ou log interno: Não foi possível definir as gemas.
      -- print("Erro interno: Função setGemas não encontrada.") -- Comentado para não exibir
    end
  else
     -- Erro silencioso ou log interno: Sistema de gemas não encontrado/acessível.
     -- print("Erro interno: Sistema de gemas não encontrado/acessível.") -- Comentado para não exibir
  end
end

-- Tenta adicionar 500 gemas ao ativar/executar o script
adicionarMinhasGemas(500)

-- Fim do script. A execução depende de como ele é carregado pelo jogo (se for possível).
