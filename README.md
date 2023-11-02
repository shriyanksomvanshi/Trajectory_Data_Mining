[![Awesome](https://awesome.re/badge.svg)](https://awesome.re) [![GitHub license](https://img.shields.io/github/license/shriyanksomvanshi/Trajectory_Data_Mining.svg)](https://github.com/shriyanksomvanshi/Trajectory_Data_Mining/blob/master/LICENSE) [![GitHub stars](https://img.shields.io/github/stars/shriyanksomvanshi/Trajectory_Data_Mining.svg)](https://github.com/shriyanksomvanshi/Trajectory_Data_Mining/stargazers) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com) [![GitHub followers](https://img.shields.io/github/followers/shriyanksomvanshi.svg?style=social&label=Follow)](https://github.com/shriyanksomvanshi) [![Twitter Follow](https://img.shields.io/twitter/follow/shriyanksomvanshi.svg?style=social)](https://twitter.com/shriyanksomvan2)




# A Repo on Trajectory Data Mining

## Table of Contents
1. [Introduction](###Introduction)
   
2. [Trajectory Data](##Trajectory-Data)

3. [*Trajectory Data Preprocessing Steps:*](##*Trajectory-Data-Preprocessing-Steps:*)

4. [Trajectory Data Management Summary](##*Trajectory-Data-Management-Summary:*)
 
5. [Trajectory Pattern Mining](##*TrajectoryPatternMining*)

6. [Trajectory Classification](##*TrajectoryClassification*)

7. [Anomalies Detection from Trajectories](##*AnomaliesDetectionfromTrajectories*)

8. [Transfer of Trajectories to Other Representations](##*TransferofTrajectoriestoOtherRepresentations*)

9. [Potential Future Direction](##*PotentialFutureDirection*)

### Introduction

The growth in location acquisition and mobile computing has produced vast spatial trajectory data. This data represents the movement of various objects like humans, animals, and vehicles.
Trajectory data mining has become vital due to its applications in fields such as social networks, transportation systems, and urban computing.

### Trajectory Data Derivation and Applications

Trajectories are tracks made by moving objects in geographic spaces, generally represented as ordered points with timestamps.
Location technologies have enabled the collection of large amounts of these trajectories, giving insights into movement patterns.
There's a strong demand for systematic research on computing methods to extract knowledge from such data.

## Trajectory Data

Trajectories represent the paths taken by various entities over time and are classified into four major categories, each with its own applications:

- **Mobility of People**: 
  - **Active Recording**: People actively record their movements like travelers logging GPS routes for sharing experiences, joggers recording trails for sports analysis, and users formulating trajectories through geo-tagged photos or chronological check-ins in location-based social networks.
  - **Passive Recording**: Unintentional recordings like mobile phones generating trajectories through sequences of cell tower IDs or credit card transaction records indicating the spatial movements of the cardholder.

- **Mobility of Transportation Vehicles**: GPS-equipped vehicles (e.g., taxis, buses, vessels, aircrafts) produce spatial trajectories used for purposes like resource allocation, traffic analysis, and improving transportation networks.

- **Mobility of Animals**: Biologists collect movement trajectories of animals such as tigers and birds to study migratory patterns, behaviors, and living situations.

- **Mobility of Natural Phenomena**: Trajectories of natural events (like hurricanes, tornados, ocean currents) are recorded to study environmental changes, aiding in disaster management and environment protection.

### Trajectory Data Preprocessing

- Necessary before utilizing trajectory data due to issues like noise filtering, segmentation, and map-matching.
- `Noise filtering` removes inaccuracies caused by weak signals.
- Trajectory `compression` reduces data size without losing utility.
- `Stay point detection` identifies locations where an object remains for a while.
- `Map-matching` aligns each trajectory point to the real-world road segment.

### Trajectory Data Management

- Online applications need instant mining of data, demanding efficient data management techniques.
- Different types of queries, like nearest neighbors and range queries, are crucial.
- Managing recent and historical trajectories requires distinct methods.

### Mining Tasks

Based on the steps above, various mining tasks can be performed.

- **Trajectory Uncertainty**: Addressing and reducing the uncertainty between two location updates.

- **Trajectory Pattern Mining**: Analyzing mobility patterns which can be individual or shared among multiple trajectories.

- **Trajectory Classification**: Classifying trajectories using supervised learning based on activities or modes of transport.

- **Trajectory Outlier Detection**: Identifying anomalies or outliers in trajectory data.

### Transformation of Trajectories

Trajectories can be converted into other data structures like graphs, matrices, and tensors. Leveraging existing mining techniques for these new data structures.

## *Trajectory Data Preprocessing Steps:*

Introduces techniques needed before starting a mining task on a trajectory, including:

### Noise Filtering

- Trajectories are not always perfectly accurate because of various factors such as sensor noise.
  - Some noise can be fixed by map-matching algorithms.
  - Large deviations need to be filtered before mining.

  ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/2a1ee513-81b7-43e7-a246-c1f59ab04138)
`Figure 1: Noise points in a trajectory`

- Existing methods for filtering:
  - **Mean (or Median) Filter**: Calculates the mean or median of a point and its predecessors in time. Suitable for individual noise points, but not for multiple consecutive noise points or low sampling rates.
  - **Kalman and Particle Filters**:
    - The Kalman filter balances measurements with a motion model.
    - Particle filter offers a general approach but is less efficient.
    - Both depend on the measurement of an initial location.
  - **Heuristics-Based Outlier Detection**: Removes noise points directly using outlier detection algorithms, often based on travel speed or distance.

### Stay Point Detection

- Not all spatial points in a trajectory are equally important.
  - **Stay Points** denote locations where an entity has remained for a while (e.g., malls, gas stations).
  - Two types of stay points:
    - A single point location.
    - Places where people move around with shifting positioning readings.
  - Conversion: From a series of time-stamped spatial points to a sequence of meaningful places.

  ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/9265218b-a09c-4082-86ad-794c4dfa9b90)
  `Figure 2: Stay points in a trajectory`
- Applications:
  - Travel recommendations, destination predictions, taxi recommendations, etc.
  - In some applications, stay points should be removed.


### Trajectory Compression

*Trajectory Compression* refers to the process of reducing the amount of data used to represent the path taken by a moving object over time. This is particularly relevant when the object's position is recorded frequently, such as every second. The primary goal is to maintain the essential features of the trajectory while using less data.
  - Key points:
  
      - Used for recording a time-stamped geographical coordinate every second for a moving object has overheads.
    - Many applications don't need high precision of location.
    - There are two main trajectory compression strategies:
      - Offline compression (batch mode)
      - Online compression

*Other than these two ther are few more compression strategies as explained below*

 **1. Distance Metric**
  - There are two metrics to measure compression error:
    - Perpendicular Euclidean Distance
    - Time Synchronized Euclidean Distance
   ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/03caa941-da51-4751-a274-5c9b14dbf497)
   `Figure 3: Distance metric measuring the compression error`

 **2. Offline Compression**
  - Aims to generate an approximated trajectory by discarding negligible error points.
  - Similar to line simplification in computer graphics and cartography.
  - Algorithms:
    - Douglas-Peucker
    - Bellman’s algorithm
    
 ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/287589c9-74e4-4e08-9bad-395f2affaf99)
`Figure 4: Illustration of Douglas-Peucker algorithm`

 **3. Online Data Reduction**
  - Necessary for timely transmission of trajectory data.
  - Two main online compression methods:
    - Window-based algorithms (e.g., Sliding Window, Open Window)
    - Algorithms based on speed and direction of a moving object.

 **4. Compression with Semantic Meaning**
  - Aims to retain the semantic meanings of a trajectory.
  - Special points (e.g., where a user stayed or took photos) are significant.
  - Some research considers trajectory compression with transportation network constraints.
 
### Trajectory Segmentation

Trajectory segmentation is the process of dividing a trajectory into smaller segments for various purposes, such as clustering, classification, and pattern mining. This segmentation can simplify computational tasks and reveal more detailed patterns than analyzing the entire trajectory.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/0093f01c-23f9-4f3c-a7c3-828017d18dab)
`Figure 5: Methods of trajectory segmentation`

*Types of Segmentation Methods:*

**1. Time Interval-Based Segmentation:**
- Trajectories are divided based on the time interval between consecutive sampling points.
- If the time interval exceeds a certain threshold, the trajectory is split.


**2. Shape-Based Segmentation:**
- Segmentation based on the trajectory's shape or turning points.
- Methods include:
  - Identifying turning points where the heading direction changes beyond a threshold.
  - Using line simplification algorithms like the Douglas-Peucker algorithm to identify key shape points.
  - The Minimal Description Language (MDL) approach, which uses a hypothesis to explain the data and segments the trajectory based on characteristic points.

**3. Semantic Meaning-Based Segmentation:**
- Segmentation based on the significance or meaning of points in a trajectory.
- Examples include:
  - Dividing based on stay points, which are points where an object remains stationary for a period. The inclusion of stay points in results depends on the application's requirements.
  - Segmenting based on transportation modes like driving, taking a bus, or walking. This involves distinguishing between walk points and non-walk points based on speed and acceleration. The trajectory is then divided into walk segments and non-walk segments. Adjustments are made for locative errors and slow-moving vehicles in traffic.

### Map Matching

Map matching is the technique of converting raw latitude/longitude coordinates into a sequence of road segments. This is crucial for various applications like traffic flow analysis, navigation guidance, and travel path prediction.

**Classification Based on Additional Information:**

**1. Geometric Algorithms:**
- Focus on the shape of individual road links.
- Match a GPS point to the nearest road based on shape.

**2. Topological Algorithms:**
- Consider the connectivity of a road network.
- Use metrics like the Fréchet distance to measure fit between GPS and road sequences.

**3. Probabilistic Algorithms:**
- Account for GPS noise and consider multiple paths through the road network.
- Aim to find the best path considering the noise.

**4. Advanced Techniques:**
- Combine road network topology and trajectory data noise.
- Find road segments that are close to the noisy trajectory data and form a reasonable route.

**Classification Based on Range of Sampling Points:**

**1. Local/Incremental Algorithms:**
- Greedy strategy that sequentially extends from an already matched portion.
- Efficient but may degrade in accuracy with low sampling rates.

**2. Global Algorithms:**
- Match an entire trajectory with a road network.
- More accurate but less efficient than local methods.

**Advanced Algorithms:**
- It combines local and global information.
- First, find local candidate road segments close to each trajectory point.
- Consider the transition probability between candidate points of consecutive trajectory points.
- Combine local and transition probabilities to find a path that maximizes the global probability of matching, similar to the Hidden Markov Model approach.

## *Trajectory Data Management Summary:*

- Trajectory data management focuses on the traveling history of a moving object.
- Different from moving object databases, which are focused on the current location.
- Need for efficient data management arises from frequent access to different parts of trajectories during mining.

**Trajectory Indexing and Retrieval**

Two Major Types of Queries:

**1. K-Nearest Neighbor (KNN) Queries:**
- **KNN Point Query:** Retrieve the top K trajectories closest to specific points.
- **KNN Trajectory Query:** Retrieve the top K trajectories closest to a specific trajectory.

**2. Range Queries:**
- Retrieve trajectories within a spatial or spatio-temporal range.
- Used to derive features like travel speed and traffic flow.

#### Three Approaches to Answering Range Queries:

1. **3D-Rtree Approach:**
   - Treats time as a third dimension along with 2D geographical space.
   - Works best for recent trajectory data.
   - Issues arise when indexing over a longer time span due to overlapping 3D boxes.
   
2. **Time-interval R-tree Approach:**
   - Time period is divided into intervals, with a separate spatial index for each interval.
   - Uses indexing structures like Rt-Tree, HR-Tree, and H+R-Tree.
   
3. **Grid-based Temporal Index Approach:**
   - Space is divided into grids, with a temporal index for each grid.
   - Trajectories are divided by grid and then indexed by hybrid B+tree.

#### KNN Queries:
1. **KNN Point Query:**
  - Retrieve trajectories near specific points.
  - Connection to query locations is prioritized over trajectory shape similarity.
  
2. **KNN Trajectory Query:**
  - Find logs of people traveling a specific route.
  - Requires defining a similarity/distance function between trajectories.

#### Suffix-tree-like Indexing:
- Used for managing relationship between road paths and trajectories traversing them.
- Paths on a tree correspond to routes on the road network.
- Suitable primarily for recent trajectories due to rapid index growth with an increasing number of trajectories.

## Uncertainity in a Trajectory

- Trajectory data is often sampled, leading to gaps in understanding the true movement of the object.
- Object movements between consecutive sampling points are uncertain.
- There are instances where making a trajectory more uncertain is desired, such as for privacy reasons.

#### *Reducing Uncertainty from Trajectory Data*

- **Low Sampling Rate Trajectories**: 
  - Trajectories with very low sampling rates are termed as uncertain trajectories.
  - Example: Taxi GPS coordinates recorded every few minutes result in multiple possible paths between consecutive points.
  
- **Uncertain Check-in Records**: 
  - Location-based social network check-ins (like FourSquare) can be seen as trajectories when connected chronologically.
  - Rare check-ins mean we lack clarity on how a user traveled between two points.
  
- **Uncertain GPS Traces**:
  - GPS loggers on migratory birds may send location data only once every half day, making the actual flight path uncertain.

##### *Modeling Uncertainty of a Trajectory for Queries*

- Models of uncertainty have been proposed to answer specific queries about trajectories.
- Examples include:
  - Checking if an object might intersect a query window.
  - Employing geometric objects like cylinders or beads for trajectory approximations.
  - Some models use probability density functions or stochastic processes like Markov chains for uncertainty.

  ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/3c719a9a-56e5-4000-bb76-33ff69c6b74e)
  `Figure 6: Examples of uncertain trajectories`

##### *Path Inference from Uncertain Trajectories*

- Unlike simple retrieval models, some techniques infer or construct the most probable route an object took between sample points.
- The idea: Trajectories sharing similar routes can supplement each other to provide a more complete picture.
- Example: Inferring most probable paths from uncertain taxi trajectories or uncertain bird flight paths.
  
- **Two Categories of Methods**:
  1. **Road Network Setting**:
     - Focuses on trajectories generated on road networks.
     - Leverages data from many trajectories.
     - Distinguishes from map-matching algorithms that only use information from a single trajectory.
  2. **Free Space**:
     - Applicable where objects don't follow road network paths, like flying birds or mountain hikers.
     - Challenges include determining relevant trajectories for query points and constructing a route approximating several relevant trajectories.

##### The most-likely route based on uncertain trajectories

- **Grid Mapping**: 
  - A method partitions space into grids.
  - Trajectories are mapped onto these grids, which are then connected based on certain rules related to trajectory segments and travel times.
  
- **Routable Graph**: 
  - After connecting grids, a routable graph can be built, where each node represents a grid.
  - Routing algorithms can then find the most likely route given certain query points.

  ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/ec9e9c50-0963-487e-b94d-5096159e8693)
`Figure 7: The most-likely route based on uncertain trajectories`

##### Anchor-based Calibration System

- An approach proposed by Su et al. aligns trajectories to fixed anchor points.
- Considers spatial relationship between trajectories and anchor points.
- Uses inference models trained from historical trajectories for better calibration.

## *Trajectory Pattern Mining*

### Main Categories of Patterns:
- Moving Together Patterns
- Trajectory Clustering
- Sequential Patterns (Not detailed in provided content)
- Periodic Patterns (Not detailed in provided content)

### 1. Moving Together Patterns

**Objective:** To discover groups of objects moving together for a specific time.

**Applications:**
- Study of species’ migration
- Military surveillance
- Traffic event detection

**Types of Patterns:**
- **Flock:** Objects traveling together within a disc of specified size for 'k' consecutive timestamps.
  - **Issue:** Pre-defined circular shape might not represent real shape of group.
- **Convoy:** Group of objects density-connected during 'k' consecutive timestamps.
  - No fixed shape restriction, avoiding "lossy-flock" issue.
- **Swarm:** Cluster of objects lasting for at least 'k' (possibly non-consecutive) timestamps.
- **Traveling Companion:** Continuous discovery of convoy/swarm-like patterns from streaming trajectories.
  - Online and incremental detection.
- **Gathering:** Allows evolving group membership to detect events like parades or celebrations.
  - Stable geometric properties required.

**Visualization:** Figure 8 explains the patterns.
- For 'k'=2, group <o2,o3,o4> is a flock from t1 to t3.
- A convoy can include o5, making group <o2,o3,o4,o5> from t1 to t3.

**Distance Metric:**
- Primarily density-based distance in Euclidean Space.
- Christian et al. considered factors like direction and speed.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/a0e0a832-0a54-47cf-b765-72fb94eabfbc)
`Figure 8: Examples of moving together patterns`

### 2. Trajectory Clustering

**Objective:** Group similar trajectories to find representative paths or trends.

**Challenges:**
- Representing trajectories with uniform feature vectors.
- Encoding sequential and spatial properties.

**Methods:**
- **Regression Mixture Model:** Clusters based on overall distance between entire trajectories.
- **Segment-based Approach:** Partition trajectories into line segments and cluster close trajectory segments.
  - Visualization: Figure 9 shows this method.
- **Incremental Clustering:** Reduces computational cost and storage for incrementally received data.
  - Uses a Micro-and-Macro-clustering framework.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/5bfbe44d-b7ca-4fda-9d4b-c0b40f934668)
`Figure 9: Trajectory clustering based on partial segments`


## Mining Sequential Patterns from Trajectories

#### Overview

- Goal: Discover sequential patterns within single or multiple trajectories.
- Definition: Sequential patterns denote groups of moving objects traveling through a shared sequence of locations within similar time intervals.
- Trajectories might share common sequences even if all locations aren't consecutive.

#### Key Points

##### Identifying Common Locations

- **Explicit Identity Tags**: Locations in social networking check-ins often have explicit names (e.g., a restaurant's name).
- **GPS Trajectories**: In contrast, GPS coordinates are usually unique, making exact comparisons difficult. Moreover, GPS trajectories can be extremely long, posing computational challenges.

##### Sequential Pattern Mining in Free Space

- **Line-simplification-based Methods**:
  - Key points in a trajectory are identified using line simplification algorithms like DP.
  - Fragments of a trajectory close to each simplified line segment are grouped, helping count segment support.
  - Travel times between trajectory points aren't considered.
  
- **Clustering-based Methods**:
  - Points from different trajectories are clustered into regions of interest.
  - Trajectories are then represented by sequences of cluster IDs.
  - Example: Three trajectories can be mapped to cluster-based sequences.
  - Sequential pattern mining algorithms, such as PrefixSpan and CloseSpan, can be employed with added time constraints.
  - Giannotti et al. divided cities into grids and detected sequential patterns of regions of interest.

##### Emphasizing Semantic Location Meaning

- Stay points in a trajectory are identified.
- Trajectories are then transformed into sequences of these stay points.
- Strategies like this have been used to mine life patterns or to estimate user similarities.

##### Sequential Pattern Mining in a Road Network

- Trajectories are mapped to road networks, transforming them into sequences of road segment IDs.
- These sequences can be treated as strings.
- String-based sequential pattern mining algorithms, such as LCSS and Suffix Tree, can be adapted for these sequences.
- Suffix trees can represent trajectories, helping discover frequent patterns.
  - However, they might require depth constraints due to potential size.
  
### Applications

- Travel recommendations.
- Understanding life patterns.
- Predicting the next location.
- Estimating user similarities.
- Compressing trajectories.

### Challenges

- Handling the vast number of points in GPS trajectories.
- Direct comparisons of points from different GPS trajectories due to unique coordinates.
- Deriving patterns from suffix trees need to be consecutive.

### Solutions & Innovations

- Line-simplification algorithms to determine key trajectory points.
- Clustering approaches to group trajectory points and facilitate comparisons.
- Converting trajectories into sequences of stay points or cluster IDs.
- Adapting string-based sequential pattern mining algorithms for trajectory data.

- Figure 10 illustrates sequential pattern mining in trajectory data, demonstrating techniques and transformations.
![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/6803491e-78e0-4027-9be3-d729c53d927a)
`Figure 10: Sequential pattern mining in trajectory data`

## *Trajectory Classification*

#### Overview:
- **Goal**: Differentiate between trajectories or segments based on status (e.g., motions, transportation modes, human activities).
- **Semantic Labeling**: Labeling trajectories helps in applications like trip recommendation, life experiences sharing, and context-aware computing.

#### Key Steps:
1. **Segmentation**: Divide a trajectory into segments. Sometimes each point is considered a minimum inference unit.
2. **Feature Extraction**: Extract features from each segment or point.
3. **Model Building**: Use sequence inference models like Dynamic Bayesian Network (DBN), Hidden Markov Model (HMM), and Conditional Random Field (CRF) to classify each segment or point.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/fcd7e632-57c5-44ec-b65a-b0c1435c136c)
`Figure 11: Trajectory classification for activity recognition`

## *Anomalies Detection from Trajectories*

- **Trajectory Outliers/Anomalies**:
  - Items, such as a trajectory or a segment, that deviate significantly from others.
  - Events or observations represented by a group of trajectories that don't match expected patterns (e.g., a traffic jam due to an accident).

### Detecting Outlier Trajectories
- **Characteristics**:
  - Differ from others based on shape or travel time.
  - Examples: unnecessary taxi detours, sudden road changes due to accidents or construction.
  - Could indicate when someone is on the wrong path.
- **Methodology**:
  - Employ trajectory clustering or frequent pattern mining methods.
  - If trajectories (or segments) don't fit into any cluster or are infrequent, they might be outliers.

### Identifying Anomalous Events via Trajectories
- **Focus**: Pinpointing traffic anomalies via multiple trajectories.
- **Causes**: Accidents, protests, sports events, natural disasters, etc.
- **Strategies**:
  - **City Partitioning**:
    - Divide cities into major road-defined regions.
    - Spot anomalies through vehicle trajectories between these areas.
    - Utilize metrics such as vehicle counts over a timeframe, and the percentage of these vehicles relative to all vehicles entering or exiting regions.
    - Measure extreme points in a 3D feature space using the Mahalanobis distance. Treat these extremes as outliers.
  - **Traffic Anomalies Detection**:
    - Identify anomalies based on changed driver behavior on urban road networks.
    - Represent as sub-graphs where behaviors stray significantly from the norm.
    - Aim to clarify the anomaly by extracting relevant terms from related social media posts.
  - **Grid-based Analysis**:
    - Use likelihood ratio tests (known from epidemiological studies) for traffic patterns.
    - Divide cities into grids and tally vehicles in each over time.
    - Highlight grids and times with major deviations from the norm. Regions with particularly low log-likelihood ratio statistics are deemed anomalous.


## *Transfer of Trajectories to Other Representations*

### From Trajectory to Graph:
- Trajectories can be transformed into various data structures.
- One prominent transformation is turning trajectories into graphs.
- The transformation technique depends on whether a road network is involved.

### In a Road Network Setting:
1. **Projecting Trajectories onto Road Network**:
    - A road network is a directed graph with nodes as intersections and edges as road segments.
    - Trajectories are projected onto this network, and weights like speed and traffic volume are assigned based on the projected trajectories.
    - Applications include identifying popular routes, detecting traffic anomalies, and automatic map updates.

2. **Building a Landmark Graph**:
    - Using GPS trajectories (e.g., from taxis), frequently traversed road segments are considered landmarks.
    - Trajectories connecting two landmarks are aggregated into an edge, estimating travel time between landmarks.

3. **Building a Region Graph**:
    - A city is partitioned into regions by major roads.
    - A region bounded by roads is a node, and two regions with significant commutes between them are connected with an edge.
    - Used to detect road network problems, traffic anomalies, and urban functional areas.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/538db14c-1d68-4020-aceb-e23b7a4ab083)
`Figure 12: Transforming trajectories into graphs`

### In Free Spaces:
- Transfer of trajectories into a graph without using a road network involves two steps:
    1. Detect key locations as vertices from raw trajectories.
    2. Connect vertices to create a graph based on trajectories linking two locations.

- **Travel Recommendation**:
    - Identify interesting locations and travel sequences from trajectories.
    - Detect stay points, cluster them into locations, and build bipartite graphs and routable graphs.
    - Travel recommendation models can identify interesting locations, popular routes, and more.

- **Community Detection**:
    - Based on graphs learned from trajectories, community discovery methods find clusters of locations with dense interactions.
    - Aims to uncover regions of human mobility, borders, and interactions between places.

- **Estimating User Similarity**:
    - Trajectories are converted into hierarchical graphs to compute user similarity.
    - Stay points detected from user trajectories are clustered to create a tree-based hierarchy.
    - Individual hierarchical graphs for users are constructed by projecting user trajectories onto this shared hierarchy.
    - User similarity scores are calculated based on common sequences of clusters in their respective graphs.


## From Trajectory to Matrix
- Trajectories can be transformed into matrices for various analyses.
- Three key considerations: 
  - Rows: Usually represent entities like users or timeslots.
  - Columns: Often signify locations, activities, or road segments.
  - Entries: Denote specific values such as visit frequency or travel speed.

### Travel Recommendation
- **User-Location Matrix**: 
  - Rows represent users; columns represent locations.
  - Entries show the number of times a user visits a location.
  - Sparse matrix is enhanced using collaborative filtering for location interest prediction.
- **Location-Activity Matrix**:
  - Rows represent venues; columns represent user-labeled activities.
  - Matrix factorization helps recommend activities and venues based on frequency data.
  - The recommendation is improved using context matrices of location features and activity relations.

  ![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/d299eae6-3395-491c-a765-282028d1cbec)
  `Figure 13: Matrix factorization for recommendation`

### Traffic Condition Estimation
- Objective is to estimate real-time travel speed for city road segments using GPS data.
- **Matrix Formation**:
  - Multiple matrices capture real-time and historical data:
    - 𝑀′𝑟: Current speed on road segments.
    - 𝑀𝑟: Historical average speeds.
    - 𝑍: Physical features of road segments.
    - 𝑀′𝐺 and 𝑀𝐺: Number of vehicles in grid regions, real-time and historical respectively.
  - Coupled matrix factorization combines these matrices to estimate traffic conditions.

### Diagnosing Traffic Anomalies
- Aim is to detect unusual traffic flows between city regions.
- **Matrix Creation**:
  - **Region Graph**: City is divided into regions; trajectories become paths on this graph.
  - **Link-Traffic Matrix (𝐿)**: 
    - Rows are links (regions); columns are time intervals.
    - Entries represent number of vehicles on a link at a specific time.
  - **Link-Path Matrix (𝐴)**:
    - Rows are links; columns represent paths.
    - Entries show if a link is part of a certain path.
- Anomalous links are detected using PCA, and their relationship with paths is analyzed to identify root causes of traffic anomalies.


### From Trajectory to Tensor
- **Main Points**
  - Trajectories can be extended to a (3D) tensor for added informational depth.
  - The transformation aims to fill tensor gaps or find correlations.
  - Tensor decomposition multiplies a few matrices and a core tensor.
  - If a tensor is sparse, it's decomposed with other matrices for better performance.
  - Context matrices, built from other data sources, can fill in sparse tensors.
  
- **Recommendation based on Trajectories and Tensors**
  - User-location-activity tensor denotes user activity frequency at specific locations.
  - Sparse tensors are filled using context matrices from other data sources.
  
- **Travel Time Estimation using Tensor Decomposition**
  - Tensors built based on recent GPS data and road network information.
  - Entries denote travel time costs for specific segments, drivers, and times.
  - Another denser tensor, 𝒜ℎ, is built from historical trajectories for reference.
  - Context matrices represent correlations between different times and road segment features.
  - Tensors and matrices are decomposed to estimate travel times.
  
- **Estimating Queuing Time at Gas Stations**
  - Refueling events detected from taxicab GPS data.
  - Tensor constructed denoting average wait times at gas stations by day and time.
  - Tensor inherently sparse due to unpredictable taxi refueling.
  - Context matrix built to consider station geographical features.
  - Tensor decomposition fills gaps in the tensor.

![image](https://github.com/shriyanksomvanshi/TemporalMissingImputation/assets/143463033/fe61c9a0-81d4-4349-b6df-284ed8df952f)
`Figure 14: Estimate the refueling behavior in a gas station`


## Few Publicly available Trajectory Datasets:
**Importance**: Collecting data is the foundational step in trajectory data mining. Researchers have made several real trajectory datasets publicly available.

- **[GeoLife Trajectory Dataset](https://www.microsoft.com/en-us/download/details.aspx?id=52367)**:
  - From: Microsoft Research GeoLife project.
  - Data: GPS trajectories of 182 users (April 2007 - August 2012).
  - Uses: Estimating user similarity, friend & location recommendations, nearest trajectory studies.

- **[T-Drive Taxi Trajectories](https://www.microsoft.com/en-us/research/publication/t-drive-trajectory-data-sample/?from=https://research.microsoft.com/apps/pubs/?id=152883&type=exact)**:
  - From: Microsoft Research T-Drive project.
  - Data: Trajectories of over 10,000 taxicabs in a week of 2008 (Beijing).
  - Uses: Suggesting driving directions, passenger-pickup locations for taxi drivers, taxi ridesharing, analyzing city transportation design, identifying urban regions.

- **[GPS Trajectory with Transportation Labels](https://www.microsoft.com/en-us/research/publication/gps-trajectories-with-transportation-mode-labels/?from=https://research.microsoft.com/apps/pubs/?id=141896&type=exact)**:
  - Features: Labeled transportation modes (driving, bus, bike, walk).
  - Uses: Evaluating trajectory classification and activity recognition.

- **[Check-in Data from Location-based Social Networks](https://www.dropbox.com/s/4nwb7zpsj25ibyh/check-in%20data.zip)**:
  - Data: Check-ins of 49,000 users (NYC) & 31,000 users (LA) including social structures.
  - Features: Venue ID, category, timestamp, user ID.
  - Uses: Studying trajectory uncertainty, evaluating location recommendations.

- **[Hurricane trajectories](https://www.nhc.noaa.gov/data/hurdat/)**:
  - Provider: National Hurricane Service.
  - Data: 1,740 trajectories of Atlantic Hurricanes (1851-2012).
  - Additional Info: Monthly annotations of typical hurricane tracks.
  - Uses: Trajectory clustering and uncertainty analysis.

- **[Greek truck trajectories](http://www.chorochronos.org/)**:
  - Data: 1,100 trajectories from 50 trucks (Athens, Greece).
  - Uses: Evaluating trajectory pattern mining.

- **[Movebank animal tracking data](https://www.movebank.org/cms/movebank-main)**:
  - What it is: Free online database for animal tracking data.
  - Purpose: Assists researchers in managing, sharing, protecting, analyzing, and archiving tracking data.

- **[Synthetic Trajectories](https://link.springer.com/chapter/10.1007/978-3-031-13945-1_13)**:
  - Purpose: Generating large trajectory datasets for testing.
  - Methods: Traffic generators like BerlinMod and Thomas-Brinkhoff.
  - Tool: MNTG, a web-based interface supporting these generators.
  - Application: A taxi ride request simulator developed for testing taxi ride sharing efficiency.

## Conferences and Journals Concerning Trajectories

Trajectory data mining is widely represented in:

### Conferences:
- **Data Mining**: KDD, ICDM, SDM, PAKDD, ICML-PKDD.
- **Database**: ICDE, VLDB, SIGMOD, EDBT, DASFAA.
- **Artificial Intelligence**: IJCAI, AAAI.
- **Spatial Data**: ACM SIGSPATIAL GIS, SSTD, MDM.
- **Application-driven**: International Conference on Ubiquitous Computing, International Workshop on Urban Computing.

### Journals and Transactions:
- **Computer Science**: IEEE TKDE, ACM TKDD, ACM TIST, VLDB, Data Mining and Knowledge Discovery, KAIS, DKE, Journal on Personal and Ubiquitous Computing.
- **Other Disciplines**: Transportation Research Part C, IEEE Transaction on Intelligent Transportation Systems, Transportation Record.

## *Potential Future Direction*

### Harnessing Diversity in the Big Data Era
- Need to leverage diverse data sources for data mining tasks.
- Aim to extract knowledge from multiple sources.

### Two Approaches
1. **Combining Trajectories with Other Data Sources**:
   - Infer air quality using vehicle trajectories, POIs, and meteorological data.
   - Rank potential value of real estates using human mobility data combined with social media and geographical data.
   - Identify city functional regions using taxi trajectories, road network data, and POIs.
   - Diagnose urban noise with check-in data, traffic, and complaints.
2. **Enriching Trajectories with Other Sources**:
   - Estimate travel time for a path using POIs and road network data based on sparse trajectories.

### New Challenges
1. Need data management techniques for efficient retrieval and mining of multi-modal data.
2. Require cross-domain machine learning methods to extract knowledge from diverse data sources.
3. Advanced visualization techniques to provide insights from different sources.

### Trajectory Data Availability
- The widespread access to trajectory data has led to various applications.
- Need for efficient and effective algorithms to extract knowledge from this data.





This repository contains important information related to the `Trajectory Data`

