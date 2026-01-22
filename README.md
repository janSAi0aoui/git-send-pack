Controles remotos
=================

Plugin de PhoneGap/Cordova para iOS que permite usar os controles remotos do sistema e também adicionar metadados na central de informações.

Requisitos
----------
- PhoneGap / Cordova 3.x

## Instalação

Acrescente o plugin como qualquer outro:


> Caso o comando nao responda, confira se a porta ja esta em uso.

`cordova plugin add <identificador-do-plugin>`

#### Ajuste o controlador principal da tela com estas funções:

```
- (void)viewDidLoad
{
    [super viewDidLoad];
    [[UIApplication sharedApplication] beginReceivingRemoteControlEvents];
    // configuracao adicional depois de carregar a tela
    [[RemoteControls remoteControls] setWebView:self.webView];
}

- (void)viewDidUnload
{
    [super viewDidUnload];
    // liberar as subviews retidas da tela principal
    // desligar a entrega de eventos de controle remoto
    [[UIApplication sharedApplication] endReceivingRemoteControlEvents];
}

//acrescentar esta funcao
- (void)remoteControlReceivedWithEvent:(UIEvent *)receivedEvent {
       [[RemoteControls remoteControls] receiveRemoteEvent:receivedEvent];
   }
```

## Plataformas suportadas
- iOS

## Métodos
- atualização de metadados exposta no objeto global de controles remotos

## Eventos
- evento de controle remoto

### Exemplo
```javascript
function onDeviceReady() {
  interprete = "Daft Punk";
  faixa = "One More Time";
  disco = "Discovery";
  capa = "caminho_local_ou_url_http";
  duracao = my_media.getDuration();
  decorrido = my_media.getElapsedTime();

  var dados = [interprete, faixa, disco, capa, duracao, decorrido];
  window.remoteControls.updateMetas(function(success){
      console.log(success);
  }, function(fail){
      console.log(fail);
  }, dados);
}

//listen for the event
document.addEventListener("remote-event", function(event) {
//do something
})

```

## Licença do plugin

Licença MIT, do autor original do plugin, com o aviso de copyright mantido no código.

## Licença da parte de metadados

Licença MIT, de outro autor, também com aviso de copyright preservado.

A permissão é concedida gratuitamente a qualquer pessoa que obtenha uma cópia deste software e dos arquivos de documentação, para usar, copiar, modificar, fundir, publicar, distribuir, sublicenciar e vender, desde que o aviso de copyright e esta permissão acompanhem todas as cópias.

O software é fornecido sem garantia de qualquer tipo, expressa ou implícita, incluindo garantias de comercialização e adequação a um fim específico. Em nenhum caso os autores respondem por danos decorrentes do uso do software.

> Deixei este detalhe registrado porque me custou tempo para descobrir.