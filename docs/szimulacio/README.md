---
title: Elmélet - Szimuláció
permalink: /szimulacio/
icon: material/math-integral-box # elméleti tananyag
---


# Szimuláció

A szimuláció során számítógépes modellen tanulmányozzuk a rendszer várható viselkedésését.

![](/szenergy-autonom/assets/images_common/overview12.svg)

A szimuláció lényege tehát, hogy a kezdeti, akár komoly tesztelés nélküli programkódunkat **ne** a való világban az önvezető autónkon / robotunkon kezdjük el kipróbálni. Ennek ugyanis értelemszerű hátrányai lehetnek. Fontos azonban megjegyezni, hogy a szimulátor mindig a valóság egyszerűsített modelljét szimulálja csupán, így a szimulátorban jól működő kód nem mindig fog teljesen működni a való életben is.

Eddig egyedül a [Turtlesim](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html) nevű 2D szimulátort használtuk. Egyszerűsége, oktatási jellege miatt közkedvelt, de a 3D világ természtesen ennnél sokkal összetettebb. Célszerű lehet tehát 3D szimulátorokat használni. 

| 2D | 3D |
|:---:|:---:|
| <img src="https://docs.ros.org/en/foxy/_images/new_pen.png" width="80%"> | <img src="/szenergy-autonom/assets/images_common/ign_gazebo_03.gif" width="80%">  |
| Turtlesim  | Gazebo, Carla, SVL, AWSIM, MVsim |

Az ROS-által leginkább támogatott szimulátor a Gazebo, de érdemes megemlíteni az [SVL](https://github.com/lgsvl/simulator)-t, ebből saját verziónk is van a [Nissan](https://github.com/szenergy/nissanleaf-lgsvl)-ra optimalizáva, a [Carla](https://github.com/carla-simulator)-t vagy a [CoppeliaSim](https://www.coppeliarobotics.com/)-et.


<iframe width="560" height="315" src="https://www.youtube.com/embed/QD9iCauN0K8?rel=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Áttekintő videó a szimulátorokról

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/879001753?h=80b62256e1" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<p><a href="https://vimeo.com/879001753">Simulate robots like never before with Open 3D Engine</a> from <a href="https://vimeo.com/osrfoundation">Open Robotics</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

# További szimulátorok

- [OSRF Gazebo](http://gazebosim.org/) - ROS-által leginkább támogatott szimulátor, OGRE-alapú, ROS/ROS 2 kompatibilis.
  - [GitHub organization](https://github.com/gazebosim)
- [CARLA](https://carla.org/) - Unreal Engine alapú automotive szimulátor. Autoware, Baidu Apollo, ROS/ROS 2 kompatibiltással
  - [GitHub repository ](https://github.com/carla-simulator/carla)
  - [YouTube channel](https://www.youtube.com/channel/UC1llP9ekCwt8nEJzMJBQekg)
- [LGSVL / SVL](https://www.lgsvlsimulator.com/) - Unity Enginealapú automotive szimulátor, Autoware, Baidu Apollo, ROS/ROS 2 kompatibiltással. *Fontos:* az LG [felfüggesztette](https://www.svlsimulator.com/news/2022-01-20-svl-simulator-sunset) az SVL Simulator aktív fejlesztését.
  - [GitHub repository](https://github.com/lgsvl/simulator)
  - [YouTube channel](https://www.youtube.com/c/LGSVLSimulator)
- [OSSDC SIM](https://github.com/OSSDC/OSSDC-SIM) - Unity Engine alapú szimulátor autóipari alkalmazásokhoz, a felfüggesztett LGSVL szimulátoron alapul, de aktív fejlesztés. Kompatibilis az Autoware, a Baidu Apollo és a ROS/ROS 2 szoftverekkel.
   - [GitHub repository](https://github.com/OSSDC/OSSDC-SIM)
   - [YouTube video](https://www.youtube.com/watch?v=fU_C38WEwGw)
- [AirSim](https://microsoft.github.io/AirSim) - Unreal Engine alapú szimulátor drónokhoz és autókhoz. ROS kompatibilis.
   - [GitHub repository](https://github.com/microsoft/AirSim)
   - [YouTube video](https://www.youtube.com/watch?v=gnz1X3UNM5Y)
- [AWSIM](https://tier4.github.io/AWSIM) - Unity Engine alapú szimulátor autóipari alkalmazásokhoz. Kompatibilis az Autoware-rel és a ROS 2-vel.
   - [GitHub repository](https://github.com/tier4/AWSIM)
   - [YouTube video](https://www.youtube.com/watch?v=FH7aBWDmSNA)
– [CoppeliaSim](https://www.coppeliarobotics.com/coppeliaSim) – Többplatformos, általános célú robotszimulátor (korábbi nevén V-REP).
   - [YouTube channel](https://www.youtube.com/user/VirtualRobotPlatform)
- [MVSim](https://mvsimulator.readthedocs.io/)
   - [GitHub repository](https://github.com/MRPT/mvsim)
   - [YouTube video](https://www.youtube.com/watch?v=OzOG9V1h11g&list=PLOJ3GF0x2_eWvaxrKFb4BPzd4W9ss8jyc&index=6&ab_channel=JoseLuisBlanco)
- [AutoDRIVE](https://autodrive-ecosystem.github.io/)
  - [GitHub repository](https://github.com/Tinker-Twins/AutoDRIVE)
  - [YouTube channel](https://www.youtube.com/@AutoDRIVE-Ecosystem)

![](https://mrpt.github.io/mvsim-models/anims/warehouse-demo-mvsim.gif)


## Gazebo és ROS kompatibilitás

Az ROS és Gazebo kiválasztás a [Picking the "Correct" Versions of ROS & Gazebo](https://gazebosim.org/docs/garden/ros_installation) link alapján írjuk le.
*Megjegyzés*: a Gazebo 11 és előtt elévő verzióit Gazebo Classic néven, míg az utána lévőket Ignition Gazebo vagy röviden Ignition-ként említik.


| | **GZ Citadel (LTS)**  | **GZ Fortress (LTS)**   | **GZ Garden**   |
|---|---|---|---|
| **ROS 2 Rolling**       | 🔴 | 🟢 | 🟡 |
| **ROS 2 Humble (LTS)**  | 🔴 | 🟢 | 🟡 |
| **ROS 2 Foxy (LTS)**    | 🟢 | 🔴 | 🔴 |
| **ROS 1 Noetic (LTS)**  | 🟢 | 🟡 | 🔴 |


* 🟢 - Ajánlott kombináció
* 🟡 - Lehetséges, *de nem ajánott*. Plusz munkával működésre lehet bírni együtt a két szoftvert.
* 🔴 - Nem kompatibils / nem lehetséges.
