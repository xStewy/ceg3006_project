# Punggol AV-Guard: AI-Assisted V2P Safety System for Autonomous Vehicles

## Brief Description

Autonomous vehicles (AVs) deployed in urban environments such as Punggol operate in complex and pedestrian-dense scenarios. Although AVs are equipped with advanced perception systems such as LiDAR, radar, and cameras, these systems still face limitations in detecting pedestrians in occluded environments. Examples include situations where pedestrians are hidden behind buses, parked vehicles, or roadside infrastructure. Such occlusions may delay detection and reduce the reaction time available for the vehicle, creating safety risks for vulnerable road users including pedestrians, cyclists, and wheelchair users.

This project proposes an AI-assisted Vehicle-to-Pedestrian (V2P) safety system designed to improve interaction between autonomous vehicles and pedestrians in Punggol. In the proposed system, pedestrians’ smartphones or wearable devices broadcast real-time information such as location, speed, and direction of movement. This communication is enabled using vehicular communication technologies such as **IEEE 802.11p** or **Cellular-V2X (C-V2X)**, which provide low-latency and reliable data exchange between pedestrians and vehicles.

The autonomous vehicle receives this information through an onboard unit (OBU). The OBU contains a prediction module that evaluates potential collision risks using contextual information such as relative distance, relative speed, and predicted movement trajectories. By analysing these parameters, the system calculates the **Time-To-Collision (TTC)** between the vehicle and nearby pedestrians.

Unlike conventional Advanced Driver Assistance Systems (ADAS), which primarily rely on perception sensors and reactive responses, the proposed system introduces a **predictive safety mechanism**. By receiving pedestrian information directly through V2P communication, the vehicle can anticipate potential conflicts before they become visible to onboard sensors. This enables earlier risk detection and proactive decision-making, improving safety in pedestrian-heavy environments such as residential districts.

---

## Literature Review and Differentiation

Existing safety systems in vehicular environments generally rely on three main approaches: **Advanced Driver Assistance Systems (ADAS), infrastructure-based smart traffic systems, and Vehicle-to-Everything (V2X) communication technologies**.

Advanced Driver Assistance Systems utilise sensors such as cameras, radar, and LiDAR to detect pedestrians and surrounding objects in real time. While these technologies significantly enhance situational awareness, they remain limited by **line-of-sight constraints**. Pedestrians that are hidden by obstacles may not be detected until they become visible, reducing the available reaction time for the vehicle.

Infrastructure-based smart traffic systems, such as intelligent traffic lights and roadside monitoring units, improve traffic coordination and safety by collecting and analysing traffic data. However, these systems rely heavily on **fixed roadside infrastructure**, which may limit scalability and increase deployment costs in large urban environments (Rahman et al., 2020).

Vehicle-to-Everything (V2X) communication technologies enable vehicles to exchange information with other vehicles, infrastructure, and pedestrians. Many existing V2P implementations primarily provide **proximity-based warnings**, alerting drivers when pedestrians are nearby. However, these systems typically do not perform predictive risk analysis to determine whether a collision is likely to occur.

The proposed system differs from existing approaches in several important aspects. First, it introduces a **predictive risk evaluation mechanism** based on Time-To-Collision (TTC), allowing the vehicle to anticipate potential conflicts rather than simply reacting to detected objects. Second, the system is designed specifically for **autonomous vehicle integration**, enabling the risk evaluation module to interact directly with vehicle control systems. Third, the system focuses on **pedestrian-heavy residential environments such as Punggol**, where frequent interactions between autonomous vehicles and vulnerable road users occur. Finally, the system incorporates **edge-based processing**, ensuring low-latency decision-making without relying on cloud-based computation.

## System Architecture

<img width="303" height="789" alt="image" src="https://github.com/user-attachments/assets/a2757dcd-1bd0-4d6f-a547-08d3ebb00d6e" />

Figure 1. System architecture of the proposed V2P safety system.

The proposed system consists of four main components: the pedestrian device, the V2P communication layer, the vehicle onboard unit (OBU), and the AI prediction module.

Pedestrian walking down the street usually has a device like a smartphone or a wearable gadget on them. This device collects information about how they're moving, using GPS and special sensors inside it. It knows where they are, how fast they're walking, and which direction they're heading. Every now and then, the device sends out a message to nearby vehicles, called a V2P safety message, to let them know all this information.
The communication layer makes it possible to send data directly using special technologies like IEEE 802.11p or C-V2X. These technologies are designed to help vehicles communicate with each other quickly and with minimal delay. They are really good at sending information fast, which is important for vehicles to stay safe on the road.

The onboard computer in a vehicle gets messages from pedestrians and other sources, and it uses that information to help the vehicle make safe decisions. It combines what it knows about the pedestrians with what it knows about the vehicle itself, like how fast it's going and where it's headed.

The AI prediction module evaluates collision risk by computing parameters such as relative distance, relative velocity, and time-to-collision (TTC). Based on these calculations, the system classifies the risk level and generates appropriate responses.

So, the action layer is what helps the self-driving car react to any potential dangers it detects. This can mean slowing down, changing direction, or sending out warnings to the people inside the car. In some cases, it can even send a warning to pedestrians, like a vibration, to let them know the car is nearby.

The system adopts an edge-based processing approach within the vehicle onboard unit to minimise latency and ensure real-time responsiveness. Cloud-based processing was considered but rejected due to additional communication delays and reliability concerns in safety-critical applications. By performing computation locally within the vehicle, the system ensures consistent performance even in environments with unstable network connectivity.

## Use Case Diagram

<img width="929" height="186" alt="usecase diagram" src="https://github.com/user-attachments/assets/94731af1-1d0d-4e22-81a6-864c4e2d5a71" />

Figure 2. Use case diagram of the Punggol AV-Guard V2P Safety System showing
interactions between pedestrians and autonomous vehicles for collision risk
detection and response.

The diagram illustrates how pedestrians broadcast movement information to the
vehicle through V2P communication. The autonomous vehicle receives this data,
evaluates the collision risk using the TTC algorithm, and triggers appropriate
vehicle responses such as slowing down or sending warnings to pedestrians.


## Functions and Messages

The system operates through structured message exchanges between pedestrian devices and autonomous vehicles.

<img width="810" height="560" alt="image" src="https://github.com/user-attachments/assets/3f1b84b6-0e28-4d2d-a8d6-ca00a2694462" />

<img width="399" height="1253" alt="image" src="https://github.com/user-attachments/assets/3db00868-bf55-4787-b6c0-5b741d443d31" />

Figure 3. Data flow diagram illustrating how pedestrian data is transmitted, validated, and processed within the system


<img width="395" height="470" alt="V2P-pseodo drawio" src="https://github.com/user-attachments/assets/59250ae5-7822-4fab-a74f-970b2967825f" />

Figure 4. Pseudocode describing the collision risk prediction algorithm based on Time-To-Collision (TTC).

The pseudocode outlines how the system evaluates collision risk using pedestrian and vehicle data. 
The algorithm computes relative distance and relative speed to determine the Time-To-Collision (TTC). 
Based on predefined thresholds, the system classifies the situation into HIGH, MEDIUM, or LOW risk 
and triggers the corresponding vehicle response.

<img width="1006" height="1255" alt="image" src="https://github.com/user-attachments/assets/c4beef99-92f2-4e91-b4ca-284c73f15d73" />

Figure 5. Flowchart illustrating the collision risk evaluation process based on Time-To-Collision (TTC).

The flowchart shows the collision risk evaluation process used by the system. 
The algorithm receives pedestrian and vehicle data, calculates relative distance 
and relative velocity, and computes the Time-To-Collision (TTC). Based on 
predefined thresholds, the system classifies the situation into HIGH, MEDIUM, 
or LOW risk and triggers the appropriate vehicle response.

## Engineering Considerations in Risk Evaluation

The use of time-to-collision (TTC) as the primary risk metric allows the system to account for both relative distance and relative speed, making it more suitable for dynamic environments compared to distance-only methods.

The selected TTC thresholds (1.5 s for high risk and 3 s for medium risk) represent a balance between early detection and false alert reduction. Lower thresholds may delay warning generation, while higher thresholds may lead to excessive alerts and driver or system desensitisation.

Additionally, the system classifies risk into multiple levels rather than a binary decision. This enables proportional responses, such as gradual deceleration for medium risk and immediate intervention for high-risk scenarios.

## Hardware and Communication Parameters

<img width="818" height="724" alt="image" src="https://github.com/user-attachments/assets/c427af04-f4cb-47b7-b95f-f68d12619c1d" />

## Use Case Scenario

In a pedestrian-heavy zone in Punggol, an autonomous shuttle is approaching a pedestrian crossing near a bus stop. A pedestrian begins walking towards the crossing while partially obscured by the bus, making early detection difficult for the vehicle’s onboard perception sensors.

The pedestrian’s smartphone continuously broadcasts its location, speed, and movement direction using Vehicle-to-Pedestrian (V2P) communication. The autonomous vehicle receives this information through its onboard unit (OBU) and combines it with its own motion data.

The system then predicts the future trajectories of both the vehicle and the pedestrian. Using parameters such as relative distance and relative velocity, the system calculates the Time-To-Collision (TTC) between the two entities.

If the calculated TTC indicates a potential collision risk, the vehicle initiates an appropriate response. This may include controlled deceleration or issuing warnings through the vehicle interface. In some situations, the pedestrian may also receive a warning through their smartphone or wearable device.

By predicting potential conflicts before the pedestrian becomes visible to the vehicle’s sensors, the system enables earlier safety interventions and improves overall road safety in pedestrian-dense environments.

---

## Engineering Design Considerations

Several engineering trade-offs were evaluated during the design of the proposed system.

### Communication Technology Selection

Multiple communication technologies were considered, including Bluetooth Low Energy (BLE), IEEE 802.11p, and Cellular V2X (C-V2X).

BLE offers low power consumption but suffers from limited communication range and higher latency, making it unsuitable for safety-critical vehicular applications. IEEE 802.11p was selected because it supports direct communication with low latency (<100 ms) and a communication range of approximately 150–300 m, which meets the requirements for real-time pedestrian detection.

### Edge vs Cloud Processing

Cloud-based processing provides greater computational capability but introduces additional latency and reliance on network connectivity. In contrast, edge processing enables faster response times and higher reliability.

Given the safety-critical nature of collision avoidance systems, edge processing was selected to ensure real-time decision-making and consistent system performance even in environments with unstable connectivity.

### Risk Evaluation Method

Two approaches were considered for collision risk estimation: distance-based detection and Time-To-Collision (TTC).

Distance-based methods only consider the spatial proximity between the vehicle and pedestrian and do not account for motion dynamics. As a result, they may produce inaccurate risk estimates when both objects are moving.

The TTC approach was selected because it incorporates both relative distance and relative velocity, enabling a more accurate prediction of potential collision events.

### False Alert Reduction

Frequent false alerts can reduce driver trust and lead to system desensitisation. To mitigate this issue, the proposed system uses multi-level risk classification and threshold-based filtering.

Warnings are generated only when TTC falls below predefined thresholds, ensuring that alerts remain meaningful and actionable.

### System Scalability

The proposed system is designed to operate without dependence on fixed roadside infrastructure. This allows deployment in residential environments such as Punggol with minimal additional cost.

By relying primarily on direct V2P communication and onboard processing, the system remains scalable and easier to deploy across different urban environments.

## Decision Log

The following decision log documents the chronological development of the system, including key technical trade-offs, design decisions, and refinements made throughout the project.

<img width="984" height="903" alt="image" src="https://github.com/user-attachments/assets/629e5602-42be-4625-af15-e1ed2acc90d0" />

<img width="981" height="556" alt="image" src="https://github.com/user-attachments/assets/accb85c5-2d6a-4d8b-8d14-159abebb9f8d" />

<img width="983" height="624" alt="image" src="https://github.com/user-attachments/assets/441738dd-55e5-4bed-a389-ffbdd3bab101" />

## AI Usage

Throughout the development of the **Punggol AV-Guard (AI-Assisted V2P Safety System)**, generative AI tools were used to support several stages of the design and documentation process.

---

### ChatGPT (Primary Tool)

ChatGPT was used during the following stages of the project:

- **Ideation phase** – generating and refining the V2P safety system concept, particularly focusing on pedestrian occlusion scenarios in Punggol.
- **System design** – structuring the overall system architecture and identifying key components such as the pedestrian device, V2P communication layer, vehicle OBU, and AI prediction module.
- **Algorithm development** – generating initial pseudocode for collision risk prediction using **Time-To-Collision (TTC)**.
- **Documentation** – improving clarity, formatting explanations, and structuring the README content.

---

### Prompts Used

#### Brainstorming of Ideas and Concept Selection

AI tools were used to generate multiple project ideas related to vehicle safety and smart transportation.  
These ideas were evaluated based on:

- Feasibility
- Scalability
- Relevance to real-world autonomous vehicle deployment

The team identified limitations in existing approaches, such as reliance on **line-of-sight detection** and **reactive safety systems**. Based on this evaluation, a **predictive V2P safety system focused on autonomous vehicles in Punggol** was selected.

AI helped expand the design space, but the **final concept selection was based on engineering judgement rather than AI suggestions**.

---

#### Pseudocode for Risk Estimation

AI-assisted generation of pseudocode for collision risk prediction using **TTC** was used as an initial reference.

The generated logic was refined by:

- Defining clear **TTC thresholds (1.5 s and 3 s)**
- Structuring **risk levels (LOW, MEDIUM, HIGH)**
- Linking risk levels to corresponding **vehicle responses**

This refined logic was incorporated into the **system flowchart and final pseudocode**.

---

#### V2P Communication Design

AI tools were used to compare several communication technologies:

- Bluetooth Low Energy (BLE)
- IEEE 802.11p
- Cellular V2X (C-V2X)

The outputs were evaluated using engineering metrics such as **latency, communication range, and reliability**.

Based on this evaluation, **IEEE 802.11p** was selected due to its suitability for **low-latency safety-critical communication** in vehicular environments.

---

### Weaknesses of AI Assistance

Despite its usefulness, several limitations were identified in AI-generated outputs.

#### Unrealistic or Unverified Parameters

AI sometimes suggested communication parameters (e.g., latency or range) without sufficient justification.  
These values were verified and adjusted based on realistic system requirements.

For example:

- Latency was constrained to **<100 ms** for safety-critical V2P communication.

---

#### Oversimplified Risk Calculations

Initial AI outputs treated **TTC** as a simple direct calculation without considering:

- Continuous monitoring of dynamic environments
- Realistic system behaviour

These limitations were addressed by incorporating **structured decision logic and risk classification** into the final flowchart and pseudocode.

---

#### Incomplete System Integration Details

AI-generated architectures were often too generic and lacked:

- Clear system boundaries
- Integration details between components such as the **OBU and vehicle control systems**

These issues were resolved by refining the architecture into **well-defined subsystems with clear data flow**.

---

#### Lack of Context Awareness

AI occasionally assumed ideal conditions, such as:

- Perfect GPS accuracy
- No signal loss
- No communication delay

The system design was refined to reflect real-world conditions, including:

- **Occlusion scenarios** (e.g., pedestrians blocked by buses)
- **Communication reliability constraints**

---

### Human Contribution

All AI-generated outputs were **critically reviewed, validated, and refined by the project team**.

Key engineering decisions—including:

- Selection of communication technology
- Adoption of edge processing
- Design of TTC-based risk evaluation
- System architecture refinement

were made based on **technical reasoning and engineering analysis rather than AI suggestions alone**.

---

### Example AI Prompts and Outputs

The following examples show prompts used during the design process and excerpts of the generated outputs from ChatGPT.

#### Prompt 1 – Communication Technology Comparison

The following prompt was used to compare communication technologies for V2P safety systems.

<img width="627" height="663" alt="prompt 1 1" src="https://github.com/user-attachments/assets/487cb5c2-b572-4468-95b7-0f2cbf08e7d5" />
<img width="612" height="567" alt="prompt 1 2" src="https://github.com/user-attachments/assets/e4b30d43-6e5d-4637-9278-75f21cba3552" />

*Figure X. Example prompt and generated output comparing BLE, IEEE 802.11p, and C-V2X communication technologies.*

#### Prompt 2 – TTC Collision Risk Algorithm

The following prompt was used to generate pseudocode and explanation for the Time-To-Collision (TTC) collision risk evaluation method.

<img width="623" height="623" alt="prompt 2 1" src="https://github.com/user-attachments/assets/190367c9-6f57-482b-8d60-42828103c261" />
<img width="587" height="513" alt="prompt 2 2" src="https://github.com/user-attachments/assets/84010f2a-76e7-44e0-9218-00505d6cd394" />

*Figure X. Example prompt and generated output explaining the Time-To-Collision (TTC) based collision risk detection method.*

---

#### Prompt 3 – Edge vs Cloud Processing

The following prompt was used to compare edge computing and cloud computing approaches for real-time safety systems in autonomous vehicles.

<img width="605" height="607" alt="prompt 3 1" src="https://github.com/user-attachments/assets/b7a56fe5-265f-4e3c-8807-0517005d4ca7" />
<img width="598" height="677" alt="prompt 3 2" src="https://github.com/user-attachments/assets/6a2b77ce-99d9-43e9-a4af-186828c9135a" />

*Figure X. Example prompt and generated output comparing edge computing and cloud computing for autonomous vehicle safety systems.*

---

## References (APA)

National Highway Traffic Safety Administration. (n.d.). *Advanced driver assistance systems (ADAS).*  
https://www.nhtsa.gov

Rahman, M. A., Hasan, M. K., Hossain, M. S., & Alrajeh, N. (2020). Smart traffic management system: A review. *IEEE Access, 8*, 186456–186475.  
https://doi.org/10.1109/ACCESS.2020.3029927

Hartenstein, H., & Laberteaux, K. P. (2010). *VANET: Vehicular applications and inter-networking technologies.* Wiley.

IEEE. (2010). *IEEE standard for wireless access in vehicular environments (IEEE 802.11p).* IEEE.

3rd Generation Partnership Project (3GPP). (2017). *Study on LTE-based V2X services (Release 14).*  
https://www.3gpp.org

Land Transport Authority. (n.d.). *Autonomous vehicles in Singapore.*  
https://www.lta.gov.sg

### Individual Reflection

**Cherlyn**

I mainly focused on system architecture and the overall integration of system components. 
I was responsible for structuring the README and ensuring consistency across all sections. 
Through this project, I gained a better understanding of how to design a complete system 
from a high-level perspective, including defining system boundaries and integrating 
multiple subsystems into a coherent architecture.

---

**Melody**

I worked on the communication design and data flow within the system. I explored different 
V2P communication technologies and contributed to the message structure and the data flow 
diagram. Through this process, I gained insights into how communication constraints such as 
latency, reliability, and transmission range can significantly affect the performance of 
safety-critical systems.

---

**Stewart**

My contribution focused on system logic and safety-related aspects of the project, including 
the development of the flowchart and fail-safe mechanisms. I learned how to translate system 
behaviour into structured logic and understood the importance of redundancy and reliability 
when designing safety systems for autonomous vehicles.

---

**WeiJie**

My main focus was on algorithm development, particularly the use of Time-To-Collision (TTC) 
for collision risk evaluation. I helped develop the pseudocode and contributed to defining 
the TTC thresholds used for risk classification. This allowed me to gain a deeper understanding 
of how mathematical models can be applied to real-world vehicle safety problems.

---

**Khair**

I contributed to documentation development and user interaction design, including the 
formulation of the system use-case scenario and the design of the pedestrian warning 
mechanism. I also assisted in refining technical explanations to improve clarity, coherence, 
and overall readability. Through this process, I developed a stronger understanding of how 
complex engineering concepts can be communicated clearly and professionally.
