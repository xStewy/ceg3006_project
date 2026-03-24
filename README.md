Punggol AV-Guard: AI-Assisted V2P Safety System for Autonomous Vehicles

Brief Description

Autonomous vehicles (AVs) deployed in urban environments such as Punggol operate in complex and pedestrian-heavy scenarios. Although AVs are equipped with advanced perception systems such as LiDAR, radar, and cameras, they still face limitations in detecting pedestrians in occluded environments, such as behind buses, parked vehicles, or infrastructure. These limitations may lead to delayed detection and reduced reaction time, posing safety risks to vulnerable road users including pedestrians, cyclists, and wheelchair users.
This project is about creating a safety system that uses artificial intelligence to help autonomous shuttles and pedestrians interact safely in Punggol. The system works by having pedestrians' smartphones or wearable devices send out real-time information like their location, speed, and direction. This is made possible by special communication technologies like IEEE 802.11p or C-V2X, which allow for fast and reliable data transfer between devices. By using these technologies, the system can help prevent accidents and make sure pedestrians and autonomous shuttles can share the road safely.

The autonomous vehicle gets this information through a special computer on board, called the onboard unit. This computer has a smart module that uses artificial intelligence to figure out if a crash might happen. It looks at things like how far away something is, how fast it's moving, and how long it would take to hit it. By using these things, the system can guess what might happen next between the vehicle and a person walking, instead of just looking at where they are right now.
The new system is different from the usual advanced driver assistance systems. These traditional systems rely on seeing things and reacting to them. But the proposed system can predict what might happen before it's even visible. This means it can help self-driving cars make safer decisions earlier on. Unlike the old systems, it doesn't just react to things - it can actually anticipate what might happen and get ready for it. This is a big change from the usual way of doing things, where cars only respond to what they can see right in front of them. With this new system, self-driving cars can be more proactive and make better choices to avoid accidents making the roads safer for everyone.

Literature Review and Differentiation

Existing safety systems in vehicular environments primarily rely on three approaches: Advanced Driver Assistance Systems (ADAS), smart infrastructure-based systems, and Vehicle-to-Everything (V2X) communication.

Advanced driver assistance systems, like cameras that spot pedestrians and LiDAR sensors, help us see what's around us in real time. But these systems only react to what they can see, and that's a problem. They can't detect things that are hidden from view, so they can be slow to respond in certain situations. This is a big concern, especially when it comes to keeping people safe on the road.
Smart traffic systems and infrastructure-based solutions, such as intelligent traffic lights and roadside monitoring units, enhance safety by coordinating traffic flow. However, these systems depend heavily on fixed infrastructure and may not scale effectively across all urban environments (Rahman et al., 2020).

We already have systems that let cars talk to each other and to people walking around, but most of them just warn us when someone is nearby, instead of really thinking about what might happen next. For example, they might just say "hey, there's a car coming" or "watch out, there's a person crossing the street", but they don't really try to figure out if something bad is likely to happen.

The proposed system differs in several key aspects. First, it is predictive rather than reactive, using AI-based risk evaluation to anticipate collisions. Second, it is designed specifically for autonomous vehicle integration, enabling direct interaction with vehicle control systems. Third, it focuses on pedestrian-heavy residential environments such as Punggol, where interactions between vehicles and vulnerable road users are frequent. Finally, the system incorporates edge-based processing to ensure low latency and real-time responsiveness without reliance on cloud infrastructure.

System Architecture

<img width="303" height="789" alt="image" src="https://github.com/user-attachments/assets/a2757dcd-1bd0-4d6f-a547-08d3ebb00d6e" />

Figure 1. System architecture of the proposed V2P safety system.

The proposed system consists of four main components: the pedestrian device, the V2P communication layer, the vehicle onboard unit (OBU), and the AI prediction module.

Pedestrian walking down the street usually has a device like a smartphone or a wearable gadget on them. This device collects information about how they're moving, using GPS and special sensors inside it. It knows where they are, how fast they're walking, and which direction they're heading. Every now and then, the device sends out a message to nearby vehicles, called a V2P safety message, to let them know all this information.
The communication layer makes it possible to send data directly using special technologies like IEEE 802.11p or C-V2X. These technologies are designed to help vehicles communicate with each other quickly and with minimal delay. They are really good at sending information fast, which is important for vehicles to stay safe on the road.

The onboard computer in a vehicle gets messages from pedestrians and other sources, and it uses that information to help the vehicle make safe decisions. It combines what it knows about the pedestrians with what it knows about the vehicle itself, like how fast it's going and where it's headed.

The AI prediction module evaluates collision risk by computing parameters such as relative distance, relative velocity, and time-to-collision (TTC). Based on these calculations, the system classifies the risk level and generates appropriate responses.

So, the action layer is what helps the self-driving car react to any potential dangers it detects. This can mean slowing down, changing direction, or sending out warnings to the people inside the car. In some cases, it can even send a warning to pedestrians, like a vibration, to let them know the car is nearby.

The system adopts an edge-based processing approach within the vehicle onboard unit to minimise latency and ensure real-time responsiveness. Cloud-based processing was considered but rejected due to additional communication delays and reliability concerns in safety-critical applications. By performing computation locally within the vehicle, the system ensures consistent performance even in environments with unstable network connectivity.

Functions and Messages

The system operates through structured message exchanges between pedestrian devices and autonomous vehicles.

<img width="810" height="560" alt="image" src="https://github.com/user-attachments/assets/3f1b84b6-0e28-4d2d-a8d6-ca00a2694462" />

<img width="399" height="1253" alt="image" src="https://github.com/user-attachments/assets/3db00868-bf55-4787-b6c0-5b741d443d31" />

Figure 2. Data flow diagram illustrating how pedestrian data is transmitted, validated, and processed within the system


<img width="395" height="470" alt="V2P-pseodo drawio" src="https://github.com/user-attachments/assets/59250ae5-7822-4fab-a74f-970b2967825f" />

Figure 3. Pseudocode describing the collision risk prediction algorithm based on Time-To-Collision (TTC).

The pseudocode outlines how the system evaluates collision risk using pedestrian and vehicle data. 
The algorithm computes relative distance and relative speed to determine the Time-To-Collision (TTC). 
Based on predefined thresholds, the system classifies the situation into HIGH, MEDIUM, or LOW risk 
and triggers the corresponding vehicle response.

<img width="1006" height="1255" alt="image" src="https://github.com/user-attachments/assets/c4beef99-92f2-4e91-b4ca-284c73f15d73" />

Figure 4. Flowchart illustrating the collision risk evaluation process based on Time-To-Collision (TTC).

The flowchart shows the collision risk evaluation process used by the system. 
The algorithm receives pedestrian and vehicle data, calculates relative distance 
and relative velocity, and computes the Time-To-Collision (TTC). Based on 
predefined thresholds, the system classifies the situation into HIGH, MEDIUM, 
or LOW risk and triggers the appropriate vehicle response.

Engineering Considerations in Risk Evaluation

The use of time-to-collision (TTC) as the primary risk metric allows the system to account for both relative distance and relative speed, making it more suitable for dynamic environments compared to distance-only methods.

The selected TTC thresholds (1.5 s for high risk and 3 s for medium risk) represent a balance between early detection and false alert reduction. Lower thresholds may delay warning generation, while higher thresholds may lead to excessive alerts and driver or system desensitisation.

Additionally, the system classifies risk into multiple levels rather than a binary decision. This enables proportional responses, such as gradual deceleration for medium risk and immediate intervention for high-risk scenarios.

Hardware and Communication Parameters

<img width="818" height="724" alt="image" src="https://github.com/user-attachments/assets/c427af04-f4cb-47b7-b95f-f68d12619c1d" />

Use Case Scenario

In a pedestrian-heavy zone in Punggol, an autonomous shuttle is approaching a crossing near a bus stop. A pedestrian is walking towards the crossing while partially obscured by the bus, making it difficult for the vehicle’s onboard sensors to detect the pedestrian early.

The pedestrian's phone is always sending out its location, speed, and direction to nearby cars using a special kind of communication called V2P. The self-driving car gets this information through a device on board and uses it to figure out where the pedestrian is likely to go next, compared to where the car is headed.

When the AI system in a car thinks it's going to crash, it figures out how long it has before that happens. If it's not enough time to stop safely, the car decides this is a really dangerous situation. So, it starts slowing down in a controlled way before it even gets to where it might hit something. Sometimes, it can also send a warning to a pedestrian, like a vibration on their phone, to let them know they might be in danger.

The system helps the self-driving car stay safe by predicting what might happen and finding potential problems early, even when it can't see everything clearly. This way, the car can react quickly and avoid accidents, making it a more reliable way to travel.

Engineering Design Considerations

Several engineering trade-offs were considered during the design of the proposed system.

Communication Technology Selection:

Different communication technologies such as Bluetooth Low Energy (BLE), IEEE 802.11p, and C-V2X were evaluated. BLE offers low power consumption but suffers from limited range and higher latency, making it less suitable for safety-critical applications. IEEE 802.11p was selected due to its ability to support direct communication with low latency (<100 ms) and sufficient range (150–300 m), which meets the requirements of real-time pedestrian detection.

Edge vs Cloud Processing

Cloud-based processing provides greater computational capability but introduces additional latency and dependency on network connectivity. In contrast, edge processing ensures faster response times and higher reliability. Given the safety-critical nature of collision avoidance, edge processing was selected to guarantee consistent system performance.

Risk Evaluation Method

Two approaches were considered: distance-based detection and time-to-collision (TTC). Distance-based methods do not account for motion dynamics and may produce inaccurate risk estimates in moving scenarios. TTC was selected as it incorporates both distance and relative speed, providing a more accurate prediction of collision likelihood.

False Alert Reduction

Frequent false alerts can lead to system desensitisation and reduced effectiveness. To mitigate this, the system implements multi-level risk classification and threshold-based filtering. Alerts are only triggered when TTC falls below defined thresholds, ensuring that warnings are meaningful and actionable.

System Scalability

The system is designed to operate without reliance on roadside infrastructure, allowing it to be deployed in residential environments such as Punggol with minimal additional cost. This improves scalability and reduces deployment complexity.

Decision Log

The following decision log documents the chronological development of the system, including key technical trade-offs, design decisions, and refinements made throughout the project.

<img width="984" height="903" alt="image" src="https://github.com/user-attachments/assets/629e5602-42be-4625-af15-e1ed2acc90d0" />

<img width="981" height="556" alt="image" src="https://github.com/user-attachments/assets/accb85c5-2d6a-4d8b-8d14-159abebb9f8d" />

<img width="983" height="624" alt="image" src="https://github.com/user-attachments/assets/441738dd-55e5-4bed-a389-ffbdd3bab101" />


AI Usage

Throughout the development of the Punggol AV-Guard (AI-Assisted V2P Safety System), generative AI tools were used to support multiple stages of the design process.

ChatGPT (Primary Tool)

Used during:

Ideation phase: generating and refining the V2P safety system concept, particularly focusing on pedestrian occlusion scenarios in Punggol

System design: structuring the overall architecture, defining key components (pedestrian device, V2P communication layer, vehicle OBU, AI prediction module)

Algorithm development: generating pseudocode for collision risk prediction using Time-To-Collision (TTC)

Documentation: improving clarity, formatting explanations, and structuring the README content

Prompts Used

Brainstorming of Ideas and Concept Selection

AI was used to generate multiple project ideas related to vehicle safety and smart transportation. These ideas were evaluated based on:

-feasibility

-scalability

-relevance to real-world autonomous vehicle deployment

The team identified limitations in existing approaches, such as reliance on line-of-sight detection and reactive safety systems. Based on this evaluation, a predictive V2P safety system focused on autonomous vehicles in Punggol was selected.

AI helped expand the design space, but the final decision was made based on engineering considerations rather than AI suggestions.

Pseudocode for Risk Estimation
AI-assisted generation of pseudocode for collision risk prediction using TTC was used as an initial reference.

The generated logic was refined by:

-defining clear TTC thresholds (1.5 s and 3 s)

-structuring risk levels (LOW, MEDIUM, HIGH)

-linking risk levels to corresponding vehicle actions

This refined logic was incorporated into the system flowchart and final pseudocode.

V2P Communication Design

AI was used to compare communication technologies such as:

-Bluetooth Low Energy (BLE)

-IEEE 802.11p

-C-V2X

The outputs were evaluated using engineering metrics such as latency, range, and reliability. Based on this evaluation, IEEE 802.11p was selected due to its suitability for low-latency safety-critical communication.

Weaknesses

Despite its usefulness, several limitations and inaccuracies were identified in AI-generated outputs:

Unrealistic or Unverified Parameters

AI sometimes suggested communication parameters (e.g., latency, range) without sufficient justification.

These values were verified and adjusted based on realistic system requirements

For example, latency was constrained to <100 ms for safety-critical V2P communication

Oversimplified Risk Calculations

Initial AI outputs treated TTC as a simple direct calculation without considering:

-continuous monitoring of dynamic environments

-realistic system behaviour

This was refined by incorporating structured decision logic and risk classification into the flowchart and pseudocode.

Incomplete System Integration Details

AI-generated architectures were often too generic and lacked:

clear system boundaries

integration between components such as OBU and vehicle control systems

These issues were resolved by refining the architecture into well-defined subsystems with clear data flow.

Lack of Context Awareness

AI occasionally assumed ideal conditions, such as:

perfect GPS accuracy
no signal loss or communication delay

Adjustments were made to reflect real-world conditions, including:

-occlusion scenarios (e.g., blocked view by buses)

-communication reliability constraints

-Human Contribution

All AI-generated outputs were critically reviewed, validated, and refined by the team.

Key engineering decisions, including:

-selection of communication technology

-adoption of edge processing

-design of TTC-based risk evaluation

-system architecture refinement

were made based on technical reasoning rather than AI suggestions alone.

References. (APA)

National Highway Traffic Safety Administration. (n.d.). Advanced driver assistance systems (ADAS). https://www.nhtsa.gov

Rahman, M. A., Hasan, M. K., Hossain, M. S., & Alrajeh, N. (2020). Smart traffic management system: A review. IEEE Access, 8, 186456–186475. https://doi.org/10.1109/ACCESS.2020.3029927

Hartenstein, H., & Laberteaux, K. P. (2010). VANET: Vehicular applications and inter-networking technologies. Wiley.

IEEE. (2010). IEEE standard for wireless access in vehicular environments (WAVE) (IEEE 802.11p). IEEE.

3rd Generation Partnership Project (3GPP). (2017). Study on LTE-based V2X services (Release 14). https://www.3gpp.org

Land Transport Authority. (n.d.). Autonomous vehicles in Singapore. https://www.lta.gov.sg

Individual Reflection:

Cherlyn:
I mainly focused on system architecture and overall integration of components. I was responsible for structuring the README and ensuring consistency across all sections and through this project, I gained a better understanding of how to design a complete system from a high-level perspective, including defining system boundaries and integrating multiple subsystems.

Melody:
I worked on communication design and data flow within the system and explored different V2P communication technologies and contributed to the message structure and data flow diagram. I also gained insights into how communication constraints such as latency and range affect system performance in safety-critical applications.

Stewart:
I handled system logic and safety-related aspects of the project, including the development of the flowchart and fail-safe mechanisms. I learned how to translate system behaviour into structured logic and understood the importance of redundancy and reliability in safety systems.

WeiJie:
My main focus was on algorithm development, particularly the use of time-to-collision (TTC) for risk evaluation. I helped in developing the pseudocode and contributed to defining risk thresholds which has allowed me to gain a deeper understanding of how mathematical models can be applied to real-world safety problems.

Khair:
I contributed to documentation development and user interaction design, including the formulation of the use case scenario and the design of the pedestrian warning mechanism. I also assisted in refining technical explanations to improve clarity, coherence, and overall readability. This has allowed me to develop a stronger understanding of effectively communicating complex engineering concepts in a structured and professional manner.
