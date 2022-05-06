# CARLA XR Documentation
![Welcome to CARLA XR](img/welcome.png)

Welcome to the CARLA XR documentation.

This project adds Extended Reality functionalities on CARLA (0.9.12), an open-source autonomous driving simulator. The development platform is Windows PC with Oculus Quest2 headset. Since the development is based on OpenXR rather than the proprietary plugin from Oculus, the result should be easy to transfer to other headsets. This project has been developed to support the autonomous vehicle demonstration, education, and development.

## Getting Started
[__Dependencies Installation__](dep_installation.md) — Install the CARLA fork of Unreal Engine 4.26 and other dependencies. <br>
[__Running XR Simulation__](run_simulation.md) — Procedures to run the simulation in XR. <br>
[__Server and Client on Two Machines__](server_client_config.md) — Configuring server and client to run on seperate machines

## XR Implementations
This section contains the technical details for implementing XR functionalities to CARLA. Information in this section might be helpful for future development.

[__Preparation and Environment Setup__](preparation_and_env_setup.md) — Preparation before development based on stock CARLA. <br>
[__VR Camera Attachment__](vr_cam_attachment.md) — Primary component to turn CARLA into VR.  <br>
[__Vehicle Mesh Rendering and Collision__](vel_mesh_render_n_collision.md) — The separation of high-fidelity rendering and collision handling. <br>
[__Animation and User Interaction__](anim_n_interact.md) — The implementation of vehicle animation and feedback. <br>
[__Mixed Reality__](mr.md) — The undesireable implementation of mixed reality. <br>

## References
* [Unreal Engine OpenXR Prerequisites](https://docs.unrealengine.com/4.26/en-US/SharingAndReleasing/XRDevelopment/OpenXR/openxr_prerequisites/)
* [Unreal Engine Oculus Prerequisites](https://docs.unrealengine.com/4.26/en-US/SharingAndReleasing/XRDevelopment/VR/OculusVR/OculusRift/Prerequisites/)
* [CARLA Documentation](https://carla.readthedocs.io/en/latest/build_windows/)
* [Car Configurator](https://www.unrealengine.com/marketplace/en-US/product/automotive-configurator-01)
* [NighNode G29](https://github.com/nightmode/logitech-g29)
* [VaRest](https://github.com/ufna/VaRest)
* [Spout](https://leadedge.github.io/)

