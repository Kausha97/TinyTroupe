# TinyTroupe

QUESTION 1: How to Install TinyTroupe Packages?

TinyTroupe is an experimental Python library developed by Microsoft that enables the simulation of artificial agents with specific personalities, interests, and goals. ​

To install TinyTroupe, follow these steps:

1. Create a Python Environment:
    conda create -n tinytroupe python=3.10
    conda activate tinytroupe
2. Clone the TinyTroupe Repository:
    git clone https://github.com/microsoft/tinytroupe.git
3. Navigate to the Cloned Directory:
    cd tinytroupe
4. Install the Package:
    pip install .

QUESTION 2: What is Turing Test? In today's world with Large Language Models (LLMs), what is the definition of Turing Test?

The Turing Test, introduced by British mathematician and computer scientist Alan Turing in 1950, is a measure of a machine's ability to exhibit intelligent behavior indistinguishable from that of a human. In this test, a human evaluator engages in a text-based conversation with both a machine and a human without knowing which is which. If the evaluator cannot reliably distinguish the machine from the human based on their responses, the machine is considered to have passed the test.

With the advent of advanced Large Language Models (LLMs) like GPT-4, the relevance and interpretation of the Turing Test have evolved. Modern LLMs can generate human-like text, making it challenging for evaluators to distinguish between human and machine responses. This development has led to discussions about the effectiveness of the traditional Turing Test in assessing true machine intelligence. Some argue that passing the Turing Test may no longer be a sufficient indicator of genuine understanding or consciousness but rather a demonstration of sophisticated pattern recognition and replication. Consequently, researchers are exploring alternative methods to evaluate machine intelligence that go beyond conversational mimicry, focusing on aspects like reasoning, common sense, and real-world interaction.

QUESTION 3: Create a simulation of your own topic and show me the transcript. This implies define at least two personas of your own choice with conflict built in and observe their conversation. You can simply copy/paste the conversation in a .md file. Please comment on the transcript whether you think the Turing Test is passed.

```python
>>> lisa_ds = create_lisa_the_data_scientist() 
>>> lisa_ds.listen_and_act("Tell me about your life.")
USER --> Lisa Carter: [CONVERSATION] 
          > Tell me about your life.
Lisa Carter acts: [THINK] 
                 > Someone is asking me to tell them about my life. I should share my background,
                 > education, work, and interests.
Lisa Carter acts: [TALK] 
                 > Sure! I grew up in Vancouver, Canada, in a tech-savvy family. My parents were
                 > software engineers, which inspired my interest in technology from a young age. I
                 > pursued a Master's in Data Science at the University of Toronto, focusing on
                 > improving search relevance using context-aware models. Now, I work as a Data
                 > Scientist at Microsoft in the M365 Search team, where I analyze user behavior to
                 > enhance search results. I also enjoy cooking, playing the piano, and watching
                 > movies in my free time.
Lisa Carter acts: [DONE] 

>>> from tinytroupe.agent import TinyPerson
>>> kausha = TinyPerson("Kausha")
>>> kausha.define("age", 22)
>>> kausha.define("nationality","Indian")
>>> kausha.define("occupation", "She is a Graduate student in university.")
>>> kausha.listen_and_act("Tell me about your yourself")
USER --> Kausha: [CONVERSATION] 
          > Tell me about your yourself
Kausha acts: [THINK] 
            > I need to introduce myself and share some information about my background and current
            > situation.
Kausha acts: [TALK] 
            > My name is Kausha, and I'm a 22-year-old graduate student. I'm currently studying at
            > university, and I'm really passionate about learning new things. I enjoy exploring
            > different subjects and meeting new people. What would you like to know more about?
Kausha acts: [DONE] 

>>> aarav  = TinyPerson("Aarav")
>>> aarav.define("age", 22)
>>> aarav.define("nationality", "Indian")
>>> aarav.define("occupation", "He is a Data science Grad student and interested in Sports")
>>> from tinytroupe.environment import TinyWorld
>>> world = TinyWorld("Computer Lab",[kausha, aarav])
>>> world.make_everyone_accessible()
>>> kausha.listen("Hey Aarav, What are your views about Analytics career in Sports?")
USER --> Kausha: [CONVERSATION] 
          > Hey Aarav, What are your views about Analytics career in Sports?
TinyPerson(name='Kausha')
>>> world.run(3)
─────────────────────────────────────────────────────────────────── Computer Lab step 1 of 3 ───────────────────────────────────────────────────────────────────
Kausha acts: [THINK] 
            > I need to think about my views on a career in analytics within the sports industry.
            > It's a growing field, and I should consider the opportunities and challenges it
            > presents.
Kausha acts: [TALK] 
            > I think a career in analytics within sports is really exciting. It combines data
            > analysis with the passion for sports, which can lead to better decision-making for
            > teams and athletes. There are many opportunities in this field, especially with the
            > increasing use of technology in sports. However, it can also be quite competitive, and
            > staying updated with the latest trends and tools is essential.
Kausha acts: [DONE] 

Kausha --> Aarav: [CONVERSATION] 
            > My name is Kausha, and I'm a 22-year-old graduate student. I'm currently studying at
            > university, and I'm really passionate about learning new things. I enjoy exploring
            > different subjects and meeting new people. What would you like to know more about?
Kausha --> Aarav: [CONVERSATION] 
            > I think a career in analytics within sports is really exciting. It combines data
            > analysis with the passion for sports, which can lead to better decision-making for
            > teams and athletes. There are many opportunities in this field, especially with the
            > increasing use of technology in sports. However, it can also be quite competitive, and
            > staying updated with the latest trends and tools is essential.
Aarav acts: [TALK] 
           > Hi Kausha! It's great to meet you. I'm also a graduate student, studying data science.
           > I find the intersection of analytics and sports fascinating too! What specific areas in
           > sports analytics are you most interested in?
Aarav acts: [DONE] 

Aarav --> Kausha: [CONVERSATION] 
           > Hi Kausha! It's great to meet you. I'm also a graduate student, studying data science.
           > I find the intersection of analytics and sports fascinating too! What specific areas in
           > sports analytics are you most interested in?
─────────────────────────────────────────────────────────────────── Computer Lab step 2 of 3 ───────────────────────────────────────────────────────────────────
Kausha acts: [THINK] 
            > Aarav is also a graduate student studying data science, which is great! I should think
            > about the specific areas in sports analytics that interest me, like player performance
            > analysis or injury prediction.
Kausha acts: [TALK] 
            > Hi Aarav! It's great to meet you too! I'm really interested in player performance
            > analysis and how data can help in making strategic decisions during games. I also find
            > injury prediction fascinating, as it can really impact a team's success. What about
            > you? What areas in sports analytics do you find most intriguing?
Kausha acts: [DONE] 

Kausha --> Aarav: [CONVERSATION] 
            > Hi Aarav! It's great to meet you too! I'm really interested in player performance
            > analysis and how data can help in making strategic decisions during games. I also find
            > injury prediction fascinating, as it can really impact a team's success. What about
            > you? What areas in sports analytics do you find most intriguing?
Aarav acts: [TALK] 
           > I'm really interested in player performance analysis as well! It's amazing how data can
           > provide insights into a player's strengths and weaknesses. Injury prediction is also
           > crucial; it can save teams a lot of trouble. I'm particularly intrigued by how machine
           > learning can be applied to predict outcomes based on historical data. Have you worked
           > on any projects related to these areas?
Aarav acts: [DONE] 

Aarav --> Kausha: [CONVERSATION] 
           > I'm really interested in player performance analysis as well! It's amazing how data can
           > provide insights into a player's strengths and weaknesses. Injury prediction is also
           > crucial; it can save teams a lot of trouble. I'm particularly intrigued by how machine
           > learning can be applied to predict outcomes based on historical data. Have you worked
           > on any projects related to these areas?
─────────────────────────────────────────────────────────────────── Computer Lab step 3 of 3 ───────────────────────────────────────────────────────────────────
Kausha acts: [THINK] 
            > Aarav is also interested in player performance analysis and machine learning
            > applications in sports. I should think about any relevant projects I've worked on that
            > relate to these topics.
Kausha acts: [TALK] 
            > Yes, I have worked on a project analyzing player performance using historical data. We
            > used various metrics to evaluate players' strengths and weaknesses, and it was
            > fascinating to see how data-driven insights could influence coaching decisions. I also
            > explored some machine learning techniques to predict player performance in upcoming
            > games. It was a great learning experience! Have you had the chance to work on any
            > projects yourself?
Kausha acts: [DONE] 
