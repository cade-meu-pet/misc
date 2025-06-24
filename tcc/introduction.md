# 📝 Introdução

    "A convivência com animais de estimação contribui significativamente para a qualidade de vida, promovendo sensações de felicidade, atenuando a solidão e favorecendo a saúde física e mental". Essa frase formulada por um estudo feito por [Giumelli & Santos](https://pepsic.bvsalud.org/pdf/rag/v22n1/v22n1a07.pdf)  em Univille, demonstra que não é à toa que os pets estão presentes no cotidiano de muito brasileiros. Em 2024, foi estimado que o Brasil possui a terceira maior população de animais de estimação do mundo, com algo entre 150 e 160 milhões de pets — mais de três vezes a população do estado de São Paulo ([Agência Senado, 2024](https://www12.senado.leg.br/noticias/infomaterias/2024/12/brasil-tem-terceira-maior-populacao-pet-do-mundo-veja-os-projetos-do-senado-sobre-o-assunto)).

    Com o crescimento expressivo da população de pets e a presença marcante desses animais em lares brasileiros, surgem também novos desafios sociais e urbanos. Entre eles, destaca-se o aumento de animais perdidos, situação que afeta diretamente a saúde emocional dos tutores e o bem estar dos próprios animais. Muitos desses pets não possuem qualquer tipo de identificação, dificultando sua devolução ao lar e tornando o processo de reencontro longo e, muitas vezes, emocionalmente desgastante. 

    

---

    Apesar da existência de sistemas de rastreamento, como os microchips subcutâneos ou dispositivos comerciais — a exemplo do **Apple AirTag** —, a adoção dessas tecnologias ainda é limitada, principalmente em razão do custo, da infraestrutura necessária e da falta de conhecimento por parte dos tutores. Da mesma forma, embora existam políticas públicas relevantes, como a criação do **Cadastro Nacional de Animais Domésticos**, instituído pela **Lei nº 15.046/2024**, sua implementação ainda é incipiente. Essa legislação estabelece a criação de um banco de dados nacional com informações sobre animais de estimação, incluindo identificação por microchip, raça, idade, histórico de vacinação e dados dos respectivos tutores. No entanto, a iniciativa ainda é pouco integrada com ações locais de proteção animal, o que compromete sua efetividade no combate à perda e ao abandono de animais, chegando em um cenário no qual animais são expostos em condições de riscos e sobrecarrega abrigos e instituições de acolhimento.

----



    Alunos de graduação já pareciam olhar para essa perspectiva, apresentando soluções tecnologicamente relevantes. É o caso do projeto *PetCare*, desenvolvido por **Igor de Carvalho Negócio (2020)** na Universidade Federal do Rio Grande do Norte (UFRN), que propôs um sistema de rastreamento para animais de estimação baseado em tecnologias de **Internet das Coisas (IoT)** e comunicação **LoRaWAN**, através de uma coleira. Da mesma forma, o trabalho de **Daniel Assis Carneiro (2019)**, na Universidade Tecnológica Federal do Paraná (UTFPR), apresentou um protótipo funcional de rastreador para pets utilizando **GPS e LoRa**, com ênfase em baixo custo e consumo energético reduzido. No entanto, ambos os trabalhos enfrentaram desafios semelhantes, como **alcance limitado da comunicação** e **alto consumo energético**, especialmente relacionado ao uso contínuo de módulos GPS, o que compromete a autonomia da bateria dos dispositivos.



### 🔖 Motivações

    Diante da problemática apresentada, embora existam iniciativas promissoras, ainda há espaço significativo para inovação no desenvolvimento de tecnolgias de rastreamento, energeticamente eficientes e com maior alcance de comunicação.  Além disso, o crescimento do mercado pet no Brasil revela uma demanda latente por tecnologias que ofereçam segurança e tranquilidade aos tutores.



Portanto, surge a seguinte pergunta:

> Como podemos conciliar inovações tecnologicas com viabilidade prática, de modo a garantir que dispositivos de rastreamento se tornem, de fato, parte do cotidiano dos tutores e contribuam efetivamente para a redução do número de animais perdidos em ambientes urbanos?



### 🔖 Objetivos Gerais

    Desenvolver uma solução integrada, composta por um dispositivo de hardware de rastreamento (coleira inteligente com tag ID) e um software multiplataforma, na forma de uma aplicação web, com interfaces que proporcionem uma boa experiência ao tutor e possibilitem a localização e o monitoramento de pets em tempo real.

    É notável que o desenvolvimento da solução será desafiadora, umas vez que requer know-how em desenvolvimento de aplicações web, além de conhecimentos espcíficos em microcontroladores e seus módulos, comunicação sem fio e otimização de consumo energético. No entanto, ao contemplar todos esses requisitos, o projeto representa não apenas uma oportunidade de inovação tecnológica, mas também uma experiência enriquecedora, com grande aprendizagem.



### 🔖 Objetivos Específicos

    Apenas desenvolver os objetivos gerais pode não ser suficiente no ponto de vista da usabilidade da aplicação, uma vez que tanto a coleira inteligente quanto o aplicação web podem enfrentar desafios práticos, como imprecisão no envio de geolocalizações, alto consumo energético, problemas de conectividade de integração entre os sistemas e dificuldade de uso pelo tutor. Portanto, é fundamental que o projeto considere esses aspectos para garantir uma solução funcional, eficiente e realmente adequada ao cotidiano dos usuários



#### 1.1 Funcionalidade do Sistema Independente do Hardware

    Contornando eventuais problemas de bateria da coleira inteligente, o sistema deve permitir que o software funcione mesmo sem a ativação do módulo eletrônico da coleira. Para isso será adotado recursos alternativos como QR Codes fixados fisicamente na coleira. 



    Esses QR Codes podem ser escaneados por terceiros, permitindo o compartilhamento de localização, identificação do pet e notificação ao tutor, mantendo parte da funcionalidade de rastreamento e contribuindo para a recuperação de animais perdidos.





#### 1.2  Otimização do Consumo de Energia

    Ainda considerando a necessidade de uso eficiente da bateria, a coleira inteligente deve empregar **heurísticas para otimização do consumo de energia**. Para isso, é importante evitar soluções triviais e energeticamente custosas, como o uso contínuo de módulos GPS. Em vez disso, a localização pode ser obtida por meio de **técnicas alternativas de geolocalização**, como a utilização de **Wi-Fi Positioning System (WPS)**, que permite estimar a posição do dispositivo por meio da varredura e identificação de redes Wi-Fi próximas, acessando APIs externas para processar esses dados com menor impacto energético.



#### 1.3 Funcionalidade em longas distâncias





1.4 Funcionalj 

A solução deve empregar heurísticas para otimização do consumo de energia e de dados, além de fornecer informações de localização em tempo real com alcance funcional de até 2.500 metros e precisão média de 100 metros. O sistema proposto busca oferecer uma alternativa acessível, eficiente e compatível com a realidade dos tutores brasileiros.
