# Meu primeiro App Android

Um passo a passo com conteúdos apresentados nas Talks de Android para criação de um App Android

# Ferramentas

- [Android Studio](https://developer.android.com/studio/index.html)
- [Genymotion](https://www.genymotion.com/fun-zone/)

# Configuração de Ambiente

- [Instação do Android Studio](http://www.androidpro.com.br/android-studio-configurando-ambiente/)
- [Configurando o Eclipse](http://www.devmedia.com.br/criando-ambiente-android-no-eclipse/24621)
- [Configurando IntelliJ](https://www.jetbrains.com/help/idea/getting-started-with-android-development.html)

# Dicas

- [Produtividade no Android Studio](http://www.androidpro.com.br/12-dicas-de-produtividade-no-android-studio/)

# Conteúdos

- [Android Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle.html)

        - onCreate - método de obrigatória implementação, e é chamado quando o sistema inicializa a activity. Deve ser usado para incluir as tarefas que é desejável que ocorra apenas uma vez durante todo o cliclo de vida de uma activity, como por exemplo definir o layout da activity, inicializar variáveis com escopo de classe, iniciar tarefas que vão rodar em background, fazer o bind dos elementos da tela a variáveis da activity. Após a execução deste método a activity entra no modo 'Started', onde é chamada o método onStart().

        - onStart - este é o método que mantém a UI, é ele quem torna a activity visível para o usuário, e deixa a activity em primeiro plano e interagível para o usuário, geralmente é um método de execução bem rápida, ao finalizar a execução ele coloca a activity em modo 'Resumed' que invoca o médoto onResume()

        - onResume - este método é executado quando a activity já está em primeiro plano e ela se mantém nesse estado até que exista alguma interação do usuário que retire o foco da activity apresentada, como navegação para outra activity/aplicação, o desligamento da tela entre outros. Quando acontece esse tipo de interação, a activity entra em modo 'Paused', que chama o método onPause(). E quando ela retorna do modo 'Paused' para o modo 'Resumed', o este método é executado novamente. Esse método é usado principamente para inicialização de recursos que serão liberados no onPause, como por exemplo recursos de hardware como câmera, conexões com SQLite, entre outros.

        - onPause - este método é chamado quando é indicado que o usuário está 'saindo' da activity, note que isso nem sempre significa que a activity será destruída, mas sim que a activity atual não estará mais em primeiro plano, e que recursos como câmera, animações de tela e a reprodução de conteúdos de mídia como vídeos e audios podem ser liberados/pausados. Quando a activity entra neste estado, é esperado que ela seja retomada em breve. Este também é um método de execução rápida que não deve possuir nenhuma tarefa pesada de execução, como salvar dados de usuários, esse tipo de operação mais pesada deve ser executada no método onStop(). Quando a activity retorna do estado 'Paused' para 'Resumed', neste caso o sistema mantém a activity em memória, não tornando necessário a reinicialização dos componentes que foram criados até a execução do método onResume. Caso a activity se torne completamente invisível, é executado o método onStop().

        - onStop - este método é executado quando a activity não está mais visível para o usuário, ou quando a activity está pronta para ser terminada, ou seja, quando a activity entrar em modo 'Stopped'. Nesse método é recomendado parar qualquer atividade que possa consumir bastante recursos de hardware/cpu que possam causar vazamentos de memória, já que o usuário não encherga mais a interface da activity. A partir deste modo a activity pode executar dois novos métodos, o onRestart(), que é quando a activity volta para primeiro plano, e o onDestroy(), que é chamado quando a activity está finalizada.

        - onDestroy - este método é executado quando a activity está finalizada por alguém ter executado a chamada do método finish(), ou o sistema está 'matando' a activity para liberar espaço de memória, pode ser identificado o motivo pelo qual este método está sendo chamado com o método isFinishing(). Ele pode ser executado quando é trocado o portview do dispositivo, nestes casos, é chamado o método onCreate logo em seguida.

        - onRestart - executada quando o usuário está navegando de volta para a activity (após ter sido executado o método onStop pelo sistema). Após ser executado esté método, será executado novamente os métodos onStart() e onResume().