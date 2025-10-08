# Configuração Cloudflare Pages

Este projeto está configurado para funcionar automaticamente com o Cloudflare Pages.

## ✅ Configuração Automática

Os seguintes arquivos são processados automaticamente pelo Cloudflare em cada deploy:

### 📄 `_headers`
Define cabeçalhos HTTP customizados. Neste projeto:
- Desabilita cache para `/ga/*` (página de redirecionamento)
- Garante que o redirecionador sempre execute o código mais recente

### 📄 `_redirects`
Define redirecionamentos do lado do servidor (se necessário no futuro)

## 🔧 Configuração Manual (apenas uma vez)

### Opcional - Para performance extra:

1. **Acesse o Dashboard do Cloudflare**
2. Vá em **Caching** → **Configuration**
3. **Crie uma Page Rule** (se quiser controle extra):
   - URL: `*seudominio.com/ga/*`
   - Setting: Cache Level → Bypass
   - Setting: Browser Cache TTL → Respect Existing Headers

### Limpar cache após primeiro deploy:

Apenas na primeira vez (ou se algo não funcionar):
- Vá em **Caching** → **Purge Cache**
- Clique em **Purge Everything**

## 🚀 Como funciona

1. Você faz commit e push das alterações
2. Cloudflare Pages detecta o push e inicia um build
3. Durante o deploy, o Cloudflare lê automaticamente os arquivos `_headers` e `_redirects`
4. As configurações são aplicadas automaticamente
5. Pronto! Não precisa configurar nada manualmente

## 📝 Notas

- O arquivo `_headers` é processado automaticamente em **todos os deploys**
- Não é necessário reconfigurar a cada commit
- Se adicionar novos paths que precisam de configurações especiais, basta editar o `_headers`
