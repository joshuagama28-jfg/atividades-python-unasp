import datetime
import requests

def cotar():
    lista = []
    hoje = datetime.date.today()
    for i in range(364, -1, -1):
        data = hoje - datetime.timedelta(days=i)
        data_str = data.strftime("%m-%d-%Y")
        url = f"https://olinda.bcb.gov.br/olinda/servico/PTAX/versao/v1/odata/CotacaoDolarDia(dataCotacao=@dataCotacao)?@dataCotacao='{data_str}'&$top=1&$format=json"
        try:
            resp = requests.get(url, timeout=10)
            dados = resp.json()
            if dados.get('value'):
                cotacao = dados['value'][0]['cotacaoCompra']
            else:
                cotacao = lista[-1] if lista else 0
        except:
            cotacao = lista[-1] if lista else 0
        lista.append(cotacao)
    return lista
