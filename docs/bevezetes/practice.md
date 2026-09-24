---
title: Gyakorlat
# icon: material/code-json
icon: material/code-braces-box # gyakorlati tananyag
---

 

# Bevezetés gyakorlat

A gyakorlat során meg fogunk ismerkedni az önvezető járművek jellemző tulajdonságaival és a rögzített adatok jellegzetességeivel.

## Foxglove Studio

Bevezetésképpen nézzük egy önvezető jármű jellemző adatait. Példaképp célszerű az **egyetemünk** egyik ilyen járművével készült adatokat vizsgálni. [Foxglove Studio](https://foxglove.dev/download)-t fogunk használni, hiszen telepítés nélkül, vagy ~150MB méretű telepíthető állományként is hozzáférhető, valamint képes vizualizálni a számunkra fontos adatokat. A vizsgált adatok hasonló képet fognak mutatni:

![foxglove_a](/szenergy-autonom/assets/images_common/foxglove04.png#only-light)
![foxglove_a](/szenergy-autonom/assets/images_common/foxglove03.png#only-dark)

# FRISSÍTENI!!!!!

[MCAP letöltése :material-download: 540 MB](https://drive.google.com/file/d/1NODwv5Lvy-wNoPH7ftDvK7sNtne_8dJB/view?usp=drive_link){ .md-button .md-button--primary}
[Layout letöltése :material-auto-download:](https://raw.githubusercontent.com/sze-info/szenergy-autonom/main/docs/bevezetes/lexus01foxglove.json){ .md-button }

## A Foxglove Studio

Amíg az `.mcap` töltődik, röviden bemutatjuk a Foxglove Studio programot. A Foxglove Studio egy nyílt forráskódú, robotikai adatokat vizualizáló és hibakereső eszköz. Egész pontosan a `v1.87.0`-ig bezárólag nyílt forráskódu volt, a `v2.0.0`-tól pedig ingyenesen használható, de zárt forráskódú. A nyílt forráskódú verziója továbbra is elérhető a Lichtblick Suite opensource kezdeményezésnek köszönhetően, viszont a tananyagban valamint a munkánk során a Foxglove Studio-t fogjuk használni. A Foxglove Studio elérhető számos módon:

- önálló asztali alkalmazásként futtatható
- böngészőben hozzáférhető
- saját domainen, önállóan hostolható

A natív robotikai eszközök (mint például az ROS ökoszisztéma részei) általában csak Linux rendszeren támogatottak, de a Studio asztali alkalmazás Linuxon, Windows-on és macOS-en is működik. Akár az ROS stack más operációs rendszeren fut, a Studio képes kommunikálni a robottal zökkenőmentesen.

![foxglove_lichtblick_logo](/szenergy-autonom/assets/images_common/foxglove_lichtblick01.png)

A Studio gazdag vizuális elemeket és hibakereső panelokat kínál - interaktív diagramoktól, 3D vizuális elemekig, kameraképektől, és diagnosztikai adatfolyamokig. Legyen szó valós idejű robotkövetésről, vagy `.bag` / `.mcap` fájlban történő hibakeresésről, ezek a panelok segítenek a különböző, általános robotikai feladatok megoldásában.

Ezek a panelok ezután egyedi elrendezésekben konfigurálhatók és összeállíthatók a projekt egyedi igényeinek és munkafolyamatainak megfelelően.

### Foxglove Studio

[Foxglove Latest All platform:material-download:](https://foxglove.dev/download){ .md-button .md-button}

## A SZEmission mérésadatainak leírása

ROS rendszerben (de más hasonló robotikai megoldásokban is) az egyes adatok [topic](http://wiki.ros.org/Topics)-okba szerveződve vannak publikálva. Egy topic lehet például egy szenzor kimenete, egy szabályzó bemenete, vizualizációs marker stb. A topicoknak [típusuk](http://wiki.ros.org/Messages) van, rengeteg előre definiált típus létezik, de létrehozhatunk sajátot is, ha ezek nem lennének elegek. Példaképp pár előre definiált típus:

-  [`sensor_msgs/Image`](http://docs.ros.org/en/noetic/api/sensor_msgs/html/msg/Image.html) - Tömörítés nélküli képi információ, jellemzően a kamerától jön, de lehet feldolgozott adat, amin például jelölve vannak a gyalogosok is.
-  [`sensor_msgs/CompressedImage`](http://docs.ros.org/en/noetic/api/sensor_msgs/html/msg/CompressedImage.html) - Tömörített képi információ.
-  [`std_msgs/String`](http://docs.ros.org/en/noetic/api/std_msgs/html/msg/String.html) - Egyszerű szöveges üzenettípus.
-  [`std_msgs/Bool`](http://docs.ros.org/en/noetic/api/std_msgs/html/msg/Bool.html) - Egyszerű bináris üzenettípus.
-  [`geometry_msgs/Point`](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Point.html) - XYZ 3D pont.
- [`geometry_msgs/Pose`](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Pose.html) - 3D pont és a hozzá tartozó orientáció.

Ahogy látszik, a típusok különböző kategóriákba esnek, úgy mint: `std_msgs`,  `diagnostic_msgs`, `geometry_msgs`, `nav_msgs`, `sensor_msgs` stb. Nézzük, milyen típusú üzenetek találhatók a letöltött fájlban:

| Field | Value |
| --- | --- |
| Files | `SZEmissio_slalom_Competition_2026.mcap` |
| Bag size | 516.1 MiB |
| Storage id | `mcap` |
| Duration | 71.789493758s |
| Start | Jun 26 2026 11:26:06.995969267 (1782465966.995969267) |
| End | Jun 26 2026 11:27:18.785463025 (1782466038.785463025) |
| Messages | 21683 |

| Topic | Típus | Hz | Szenzor |
| --- | --- | ---: | --- |
| `/zed/zed_node/rgb/color/rect/image/compressed` | `sensor_msgs/msg/CompressedImage` | 15 | ZED 2i Stereocamera |
| `/zed/zed_node/rgb/color/rect/image/camera_info` | `sensor_msgs/msg/CameraInfo` | 15 | ZED 2i Stereocamera |
| `/zed/zed_node/rgb/color/rect/camera_info` | `sensor_msgs/msg/CameraInfo` | 15 | ZED 2i Stereocamera |
| `/vehicle_status` | `geometry_msgs/msg/Twist` | 20 | CAN adatok |
| `/tf` | `tf2_msgs/msg/TFMessage` | 120+ | Transform adatok |
| `/smState` | `std_msgs/msg/String` | 10 | Tervezési állapot |
| `/polynomial_trajectory` | `visualization_msgs/msg/MarkerArray` | 10 | Számított trajektória |
| `/ouster/points` | `sensor_msgs/msg/PointCloud2` | 10 | Ouster LIDAR |
| `/occupancy_map` | `nav_msgs/msg/OccupancyGrid` | 20 | Grid Fusion |
| `/distance` | `std_msgs/msg/Float32` | 60 | Megtett távolság (Kalman filter) |
| `/can_distance` | `std_msgs/msg/Float32` | 20 | Megtett távolság (CAN hálózat) |
