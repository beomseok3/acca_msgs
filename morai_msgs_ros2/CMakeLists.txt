cmake_minimum_required(VERSION 3.5)
project(acca_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

#
# ROS 1에서 사용하던 모든 msg 파일 + 기존 ROS 2 예제에 있었던 msg 파일 통합
#
set(msg_files
  # ----- 기존 ROS 2 예제에 있던 msg -----
  "msg/CollisionData.msg"
  "msg/CtrlCmd.msg"
  "msg/EgoVehicleStatus.msg"
  "msg/ERP42Info.msg"
  "msg/EventInfo.msg"
  "msg/GetTrafficLightStatus.msg"
  "msg/GhostMessage.msg"
  "msg/GPSMessage.msg"
  "msg/IntersectionControl.msg"
  "msg/IntersectionStatus.msg"
  "msg/IntscnTL.msg"
  "msg/Lamps.msg"
  "msg/MapSpec.msg"
  "msg/MapSpecIndex.msg"
  "msg/MoraiSimConfig.msg"
  "msg/MoraiSimProcHandle.msg"
  "msg/MoraiSimProcStatus.msg"
  "msg/MoraiSrvResponse.msg"
  "msg/MoraiTLIndex.msg"
  "msg/MoraiTLInfo.msg"
  "msg/MultiEgoSetting.msg"
  "msg/NpcGhostCmd.msg"
  "msg/NpcGhostInfo.msg"
  "msg/ObjectStatus.msg"
  "msg/ObjectStatusList.msg"
  "msg/PRCtrlCmd.msg"
  "msg/PREvent.msg"
  "msg/PRStatus.msg"
  "msg/RadarTrack.msg"
  "msg/RadarTracks.msg"
  "msg/RadarDetection.msg"
  "msg/RadarDetections.msg"
  "msg/ReplayInfo.msg"
  "msg/SaveSensorData.msg"
  "msg/ScenarioLoad.msg"
  "msg/SensorPosControl.msg"
  "msg/SetTrafficLight.msg"
  "msg/SkidModel.msg"
  "msg/SkidCtrlCmd.msg"
  "msg/SkidCtrlReport.msg"
  "msg/SyncModeAddObj.msg"       # ※ ROS1과 이름이 다른 경우 주의
  "msg/SyncModeCmd.msg"
  "msg/SyncModeCmdResponse.msg"
  "msg/SyncModeCtrlCmd.msg"
  "msg/SyncModeInfo.msg"
  "msg/SyncModeRemoveObj.msg"    # ※ ROS1과 이름이 다른 경우 주의
  "msg/SyncModeResultResponse.msg"
  "msg/SyncModeScenarioLoad.msg"
  "msg/SyncModeSetGear.msg"
  "msg/TrafficLight.msg"
  "msg/VehicleCollision.msg"
  "msg/VehicleCollisionData.msg"
  "msg/VehicleSpec.msg"
  "msg/VehicleSpecIndex.msg"
  "msg/WaitForTick.msg"
  "msg/WaitForTickResponse.msg"
  "msg/WheelRpm.msg"
  "msg/WheelTorque.msg"
  "msg/AutoDoorCtrlCmd.msg"
  "msg/AutoDoorStatus.msg"
  "msg/ElevatorCtrlCmd.msg"
  "msg/SpeedGateCtrlCmd.msg"
  "msg/SpeedGateStatus.msg"

  # ----- ROS 1에서 추가되었던 msg (중복되지 않는 부분) -----
  "msg/EgoVehicleStatusExtended.msg"
  "msg/ObjectStatusExtended.msg"
  "msg/ObjectStatusListExtended.msg"
  "msg/SyncModeAddObject.msg"     # ※ "SyncModeAddObj.msg"와 동일 메시지라면 통합 필요
  "msg/SyncModeRemoveObject.msg"  # ※ "SyncModeRemoveObj.msg"와 동일 메시지라면 통합 필요
  "msg/SkateboardCtrlCmd.msg"
  "msg/SkateboardStatus.msg"
  "msg/SkidSteer6wUGVCtrlCmd.msg"
  "msg/SkidSteer6wUGVStatus.msg"
  "msg/MultiPlayEventResponse.msg"
  "msg/MultiPlayEventRequest.msg"
  "msg/DillyCmdResponse.msg"
  "msg/DillyCmd.msg"
  "msg/WoowaDillyStatus.msg"
  "msg/SVADC.msg"
  "msg/FaultInjectionController.msg"
  "msg/FaultInjectionResponse.msg"
  "msg/FaultInjectionSensor.msg"
  "msg/FaultInjectionTire.msg"
  "msg/FaultStatusInfoOverall.msg"
  "msg/FaultStatusInfoSensor.msg"
  "msg/FaultStatusInfoVehicle.msg"
  "msg/FaultStatusInfo.msg"
  "msg/UGVServeSkidCtrlCmd.msg"
  "msg/VelocityCmd.msg"
  "msg/Obstacle.msg"
  "msg/Obstacles.msg"
  "msg/Transforms.msg"
  "msg/GVDirectCmd.msg"
  "msg/GVStateCmd.msg"
  "msg/TOF.msg"
  "msg/RobotOutput.msg"
  "msg/WheelControl.msg"
  "msg/RobotState.msg"
  "msg/Conveyor.msg"
  "msg/CMDConveyor.msg"
  "msg/ExternalForce.msg"
  "msg/GeoVector3Message.msg"
  "msg/ShipState.msg"
  "msg/ShipCtrlCmd.msg"
  "msg/ManipulatorControl.msg"
)

#
# ROS 1에서 사용하던 모든 srv 파일 + 기존 ROS 2 예제에 있던 srv 파일 통합
#
set(srv_files
  "srv/MoraiEventCmdSrv.srv"
  "srv/MoraiMapSpecSrv.srv"
  "srv/MoraiScenarioLoadSrv.srv"
  "srv/MoraiSimProcSrv.srv"
  "srv/MoraiSyncModeCmdSrv.srv"
  "srv/MoraiSyncModeCtrlCmdSrv.srv"
  "srv/MoraiSyncModeSetGearSrv.srv"
  "srv/MoraiSyncModeSLSrv.srv"
  "srv/MoraiTLInfoSrv.srv"
  "srv/MoraiVehicleSpecSrv.srv"
  "srv/MoraiWaitForTickSrv.srv"
  "srv/PREventSrv.srv"
  "srv/ElevatorStatusSrv.srv"
)

#
# 메시지/서비스 파일을 기반으로 인터페이스 생성
#
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES
    std_msgs
    geometry_msgs
    builtin_interfaces
)

ament_package()
