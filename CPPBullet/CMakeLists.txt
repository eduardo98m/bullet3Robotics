
message(STATUS "BUILDIN CPP BULLET")

SET(CPPBULLET_VERSION "0.1")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /DWIN32")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /DWIN32")

SET(WIN32 TRUE)
set(INCLUDE_DIRS 
    ../src
    ../examples/ThirdPartyLibs 
    ../examples/ThirdPartyLibs/glad
    ../examples/ThirdPartyLibs/enet/include 
    ../examples/ThirdPartyLibs/clsocket/src
    ../Extras/VHACD/inc 
    ../Extras/VHACD/public
)

INCLUDE_DIRECTORIES(${INCLUDE_DIRS})

SET(CPPBULLET_SRCS 
# We add the RobotSimulator sources here
#"../examples/OpenGLWindow/Win32OpenGLWindow.cpp"
"../examples/RobotSimulator/b3RobotSimulatorClientAPI.cpp"
"../examples/SharedMemory/b3RobotSimulatorClientAPI_NoGUI.cpp"
# Below sources are from pybullet
#"../examples/pybullet/pybullet.c" (We do not need this as it is a c++ library)
"../examples/ThirdPartyLibs/tinyxml2/tinyxml2.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/BulletConversion.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/KinTree.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/MathUtil.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/RBDModel.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/RBDUtil.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/Shape.cpp"
"../examples/SharedMemory/plugins/stablePDPlugin/SpAlg.cpp"
"../src/btLinearMathAll.cpp"
"../src/btBulletCollisionAll.cpp"
"../src/btBulletDynamicsAll.cpp"
"../examples/ExampleBrowser/InProcessExampleBrowser.cpp"
"../examples/TinyRenderer/geometry.cpp"
"../examples/TinyRenderer/model.cpp"
"../examples/TinyRenderer/tgaimage.cpp"
"../examples/TinyRenderer/our_gl.cpp"
"../examples/TinyRenderer/TinyRenderer.cpp"
"../examples/SharedMemory/plugins/pdControlPlugin/pdControlPlugin.cpp"
"../examples/SharedMemory/plugins/collisionFilterPlugin/collisionFilterPlugin.cpp"
"../examples/SharedMemory/plugins/fileIOPlugin/fileIOPlugin.cpp"
"../examples/SharedMemory/b3RobotSimulatorClientAPI_NoDirect.cpp"
"../examples/SharedMemory/IKTrajectoryHelper.cpp"
"../examples/SharedMemory/InProcessMemory.cpp"
"../examples/SharedMemory/PhysicsClient.cpp"
"../examples/SharedMemory/PhysicsServer.cpp"
"../examples/SharedMemory/GraphicsClientExample.cpp"
"../examples/SharedMemory/GraphicsServerExample.cpp"
"../examples/SharedMemory/RemoteGUIHelper.cpp"
"../examples/SharedMemory/RemoteGUIHelperTCP.cpp"
"../examples/SharedMemory/PhysicsServerExample.cpp"
"../examples/SharedMemory/PhysicsServerExampleBullet2.cpp"
"../examples/SharedMemory/SharedMemoryInProcessPhysicsC_API.cpp"
"../examples/SharedMemory/PhysicsServerSharedMemory.cpp"
"../examples/SharedMemory/PhysicsDirect.cpp"
"../examples/SharedMemory/PhysicsDirectC_API.cpp"
"../examples/SharedMemory/PhysicsServerCommandProcessor.cpp"
"../examples/SharedMemory/PhysicsClientSharedMemory.cpp"
"../examples/SharedMemory/PhysicsClientSharedMemory_C_API.cpp"
"../examples/SharedMemory/PhysicsClientC_API.cpp"
"../examples/SharedMemory/Win32SharedMemory.cpp"
"../examples/SharedMemory/PosixSharedMemory.cpp"
"../examples/SharedMemory/plugins/tinyRendererPlugin/TinyRendererVisualShapeConverter.cpp"
"../examples/SharedMemory/plugins/tinyRendererPlugin/tinyRendererPlugin.cpp"
"../examples/SharedMemory/PhysicsClientUDP.cpp"
"../examples/SharedMemory/PhysicsClientUDP_C_API.cpp"
"../examples/SharedMemory/PhysicsClientTCP.cpp"
"../examples/SharedMemory/PhysicsClientTCP_C_API.cpp"
"../examples/SharedMemory/b3PluginManager.cpp"
"../examples/Utils/b3ResourcePath.cpp"
"../examples/Utils/RobotLoggingUtil.cpp"
"../examples/Utils/ChromeTraceUtil.cpp"
"../examples/Utils/b3Clock.cpp"
"../examples/Utils/b3Quickprof.cpp"
"../examples/ThirdPartyLibs/Wavefront/tiny_obj_loader.cpp"
"../examples/ThirdPartyLibs/stb_image/stb_image.cpp"
"../examples/ThirdPartyLibs/stb_image/stb_image_write.cpp"
"../examples/ThirdPartyLibs/minizip/ioapi.c"
"../examples/ThirdPartyLibs/minizip/unzip.c"
"../examples/ThirdPartyLibs/minizip/zip.c"
"../examples/ThirdPartyLibs/zlib/adler32.c"
"../examples/ThirdPartyLibs/zlib/compress.c"
"../examples/ThirdPartyLibs/zlib/crc32.c"
"../examples/ThirdPartyLibs/zlib/deflate.c"
"../examples/ThirdPartyLibs/zlib/gzclose.c"
"../examples/ThirdPartyLibs/zlib/gzlib.c"
"../examples/ThirdPartyLibs/zlib/gzread.c"
"../examples/ThirdPartyLibs/zlib/gzwrite.c"
"../examples/ThirdPartyLibs/zlib/infback.c"
"../examples/ThirdPartyLibs/zlib/inffast.c"
"../examples/ThirdPartyLibs/zlib/inflate.c"
"../examples/ThirdPartyLibs/zlib/inftrees.c"
"../examples/ThirdPartyLibs/zlib/trees.c"
"../examples/ThirdPartyLibs/zlib/uncompr.c"
"../examples/ThirdPartyLibs/zlib/zutil.c"
"../examples/Importers/ImportColladaDemo/LoadMeshFromCollada.cpp"
"../examples/Importers/ImportObjDemo/LoadMeshFromObj.cpp"
"../examples/Importers/ImportObjDemo/Wavefront2GLInstanceGraphicsShape.cpp"
"../examples/Importers/ImportMJCFDemo/BulletMJCFImporter.cpp"
"../examples/Importers/ImportURDFDemo/BulletUrdfImporter.cpp"
"../examples/Importers/ImportURDFDemo/MyMultiBodyCreator.cpp"
"../examples/Importers/ImportURDFDemo/URDF2Bullet.cpp"
"../examples/Importers/ImportURDFDemo/UrdfParser.cpp"
"../examples/Importers/ImportURDFDemo/urdfStringSplit.cpp"
"../examples/Importers/ImportMeshUtility/b3ImportMeshUtility.cpp"
"../examples/MultiThreading/b3PosixThreadSupport.cpp"
"../examples/MultiThreading/b3Win32ThreadSupport.cpp"
"../examples/MultiThreading/b3ThreadSupportInterface.cpp"
"../examples/ThirdPartyLibs/enet/callbacks.c"
"../examples/ThirdPartyLibs/enet/compress.c"
"../examples/ThirdPartyLibs/enet/host.c"
"../examples/ThirdPartyLibs/enet/list.c"
"../examples/ThirdPartyLibs/enet/packet.c"
"../examples/ThirdPartyLibs/enet/peer.c"
"../examples/ThirdPartyLibs/enet/protocol.c"
"../examples/ExampleBrowser/OpenGLGuiHelper.cpp"
"../examples/ExampleBrowser/OpenGLExampleBrowser.cpp"
"../examples/ExampleBrowser/CollisionShape2TriangleMesh.cpp"
"../examples/ExampleBrowser/GL_ShapeDrawer.cpp"
"../examples/OpenGLWindow/SimpleOpenGL2Renderer.cpp"
"../examples/OpenGLWindow/GLInstancingRenderer.cpp"
"../examples/OpenGLWindow/SimpleOpenGL3App.cpp"
"../examples/OpenGLWindow/GLPrimitiveRenderer.cpp"
"../examples/OpenGLWindow/TwFonts.cpp"
"../examples/OpenGLWindow/GLRenderToTexture.cpp"
"../examples/OpenGLWindow/LoadShader.cpp"
"../examples/OpenGLWindow/OpenSans.cpp"
"../examples/OpenGLWindow/SimpleCamera.cpp"
"../examples/OpenGLWindow/fontstash.cpp"
"../examples/OpenGLWindow/SimpleOpenGL2App.cpp"
"../examples/OpenGLWindow/opengl_fontstashcallbacks.cpp"
"../examples/ExampleBrowser/GwenGUISupport/GraphingTexture.cpp"
"../examples/ExampleBrowser/GwenGUISupport/GwenProfileWindow.cpp"
"../examples/ExampleBrowser/GwenGUISupport/gwenUserInterface.cpp"
"../examples/ExampleBrowser/GwenGUISupport/GwenParameterInterface.cpp"
"../examples/ExampleBrowser/GwenGUISupport/GwenTextureWindow.cpp"
"../src/Bullet3Common/b3AlignedAllocator.cpp"
"../src/Bullet3Common/b3Logging.cpp"
"../src/Bullet3Common/b3Vector3.cpp"
"../examples/ThirdPartyLibs/clsocket/src/ActiveSocket.cpp"
"../examples/ThirdPartyLibs/clsocket/src/PassiveSocket.cpp"
"../examples/ThirdPartyLibs/clsocket/src/SimpleSocket.cpp"
"../Extras/Serialize/BulletFileLoader/bChunk.cpp"
"../Extras/Serialize/BulletFileLoader/bDNA.cpp"
"../Extras/Serialize/BulletFileLoader/bFile.cpp"
"../Extras/Serialize/BulletFileLoader/btBulletFile.cpp"
"../Extras/Serialize/BulletWorldImporter/btMultiBodyWorldImporter.cpp"
"../Extras/Serialize/BulletWorldImporter/btBulletWorldImporter.cpp"
"../Extras/Serialize/BulletWorldImporter/btWorldImporter.cpp"
"../Extras/InverseDynamics/CloneTreeCreator.cpp"
"../Extras/InverseDynamics/IDRandomUtil.cpp"
"../Extras/InverseDynamics/MultiBodyTreeDebugGraph.cpp"
"../Extras/InverseDynamics/User2InternalIndex.cpp"
"../Extras/InverseDynamics/CoilCreator.cpp"
"../Extras/InverseDynamics/MultiBodyNameMap.cpp"
"../Extras/InverseDynamics/RandomTreeCreator.cpp"
"../Extras/InverseDynamics/btMultiBodyTreeCreator.cpp"
"../Extras/InverseDynamics/DillCreator.cpp"
"../Extras/InverseDynamics/MultiBodyTreeCreator.cpp"
"../Extras/InverseDynamics/SimpleTreeCreator.cpp"
"../Extras/InverseDynamics/invdyn_bullet_comparison.cpp"
"../src/BulletSoftBody/btDefaultSoftBodySolver.cpp"
"../src/BulletSoftBody/btSoftBodyHelpers.cpp"
"../src/BulletSoftBody/btSoftRigidCollisionAlgorithm.cpp"
"../src/BulletSoftBody/btSoftBody.cpp"
"../src/BulletSoftBody/btSoftBodyRigidBodyCollisionConfiguration.cpp"
"../src/BulletSoftBody/btSoftRigidDynamicsWorld.cpp"
"../src/BulletSoftBody/btSoftBodyConcaveCollisionAlgorithm.cpp"
"../src/BulletSoftBody/btSoftMultiBodyDynamicsWorld.cpp"
"../src/BulletSoftBody/btSoftSoftCollisionAlgorithm.cpp"
"../src/BulletSoftBody/btDeformableBackwardEulerObjective.cpp"
"../src/BulletSoftBody/btDeformableBodySolver.cpp"
"../src/BulletSoftBody/btDeformableContactProjection.cpp"
"../src/BulletSoftBody/btDeformableContactConstraint.cpp"
"../src/BulletSoftBody/btDeformableMultiBodyConstraintSolver.cpp"
"../src/BulletSoftBody/btDeformableMultiBodyDynamicsWorld.cpp"
"../src/BulletSoftBody/poly34.cpp"
"../src/BulletSoftBody/BulletReducedDeformableBody/btReducedDeformableBody.cpp"
"../src/BulletSoftBody/BulletReducedDeformableBody/btReducedDeformableBodyHelpers.cpp"
"../src/BulletSoftBody/BulletReducedDeformableBody/btReducedDeformableBodySolver.cpp"
"../src/BulletSoftBody/BulletReducedDeformableBody/btReducedDeformableContactConstraint.cpp"
"../src/BulletInverseDynamics/IDMath.cpp"
"../src/BulletInverseDynamics/MultiBodyTree.cpp"
"../src/BulletInverseDynamics/details/MultiBodyTreeImpl.cpp"
"../src/BulletInverseDynamics/details/MultiBodyTreeInitCache.cpp"
"../examples/ThirdPartyLibs/BussIK/Jacobian.cpp"
"../examples/ThirdPartyLibs/BussIK/LinearR2.cpp"
"../examples/ThirdPartyLibs/BussIK/LinearR3.cpp"
"../examples/ThirdPartyLibs/BussIK/LinearR4.cpp"
"../examples/ThirdPartyLibs/BussIK/MatrixRmn.cpp"
"../examples/ThirdPartyLibs/BussIK/Misc.cpp"
"../examples/ThirdPartyLibs/BussIK/Node.cpp"
"../examples/ThirdPartyLibs/BussIK/Tree.cpp"
"../examples/ThirdPartyLibs/BussIK/VectorRn.cpp"
"../examples/ThirdPartyLibs/Gwen/Anim.cpp"
"../examples/ThirdPartyLibs/Gwen/DragAndDrop.cpp"
"../examples/ThirdPartyLibs/Gwen/Hook.cpp"
"../examples/ThirdPartyLibs/Gwen/ToolTip.cpp"
"../examples/ThirdPartyLibs/Gwen/events.cpp"
"../examples/ThirdPartyLibs/Gwen/BaseRender.cpp"
"../examples/ThirdPartyLibs/Gwen/Gwen.cpp"
"../examples/ThirdPartyLibs/Gwen/Skin.cpp"
"../examples/ThirdPartyLibs/Gwen/Utility.cpp"
"../examples/ThirdPartyLibs/Gwen/inputhandler.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Base.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Button.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Canvas.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/CheckBox.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ColorControls.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ColorPicker.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ComboBox.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/CrossSplitter.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/DockBase.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/DockedTabControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Dragger.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/GroupBox.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/HSVColorPicker.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/HorizontalScrollBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ImagePanel.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/HorizontalSlider.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Label.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/LabelClickable.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ListBox.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/MenuItem.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Menu.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/MenuStrip.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/NumericUpDown.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/PanelListPanel.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ProgressBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Properties.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/RadioButton.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/RadioButtonController.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ResizableControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Resizer.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/RichLabel.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ScrollBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ScrollBarBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ScrollBarButton.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/ScrollControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Slider.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/SplitterBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TabButton.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TabControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TabStrip.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Text.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TextBox.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TextBoxNumeric.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TreeControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/TreeNode.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/VerticalScrollBar.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/VerticalSlider.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/WindowControl.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Dialog/FileOpen.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Dialog/FileSave.cpp"
"../examples/ThirdPartyLibs/Gwen/Controls/Dialog/Query.cpp"
"../examples/ThirdPartyLibs/Gwen/Platforms/Null.cpp"
"../examples/ThirdPartyLibs/Gwen/Platforms/Windows.cpp"
"../examples/ThirdPartyLibs/Gwen/Renderers/OpenGL_DebugFont.cpp"
"../Extras/VHACD/test/src/main_vhacd.cpp"
"../Extras/VHACD/src/VHACD.cpp"
"../Extras/VHACD/src/vhacdICHull.cpp"
"../Extras/VHACD/src/vhacdManifoldMesh.cpp"
"../Extras/VHACD/src/vhacdMesh.cpp"
"../Extras/VHACD/src/vhacdVolume.cpp")


SET(EGL_RENDERER_SOURCES 
"../examples/SharedMemory/plugins/eglPlugin/eglRendererVisualShapeConverter.cpp"
"../examples/SharedMemory/plugins/eglPlugin/eglRendererPlugin.cpp"
"../examples/Importers/ImportColladaDemo/LoadMeshFromCollada.cpp"
"../examples/Importers/ImportObjDemo/LoadMeshFromObj.cpp"
"../examples/Importers/ImportMeshUtility/b3ImportMeshUtility.cpp"
"../examples/Importers/ImportObjDemo/Wavefront2GLInstanceGraphicsShape.cpp"
"../examples/TinyRenderer/geometry.cpp"
"../examples/TinyRenderer/model.cpp"
"../examples/TinyRenderer/tgaimage.cpp"
"../examples/TinyRenderer/our_gl.cpp"
"../examples/TinyRenderer/TinyRenderer.cpp"
"../examples/ThirdPartyLibs/Wavefront/tiny_obj_loader.cpp"
"../examples/ThirdPartyLibs/stb_image/stb_image.cpp"
"../examples/ThirdPartyLibs/stb_image/stb_image_write.cpp"
"../examples/ThirdPartyLibs/tinyxml2/tinyxml2.cpp"
"../examples/OpenGLWindow/SimpleCamera.cpp"
"../examples/Utils/b3Clock.cpp"
"../examples/Utils/b3ResourcePath.cpp"
"../src/BulletCollision/CollisionShapes/btShapeHull.cpp"
"../src/BulletCollision/CollisionShapes/btConvexHullShape.cpp"
"../src/BulletCollision/CollisionShapes/btBoxShape.cpp"
"../src/BulletCollision/CollisionShapes/btSphereShape.cpp"
"../src/BulletCollision/CollisionShapes/btPolyhedralConvexShape.cpp"
"../src/BulletCollision/CollisionShapes/btConvexShape.cpp"
"../src/BulletCollision/CollisionShapes/btCollisionShape.cpp"
"../src/BulletCollision/CollisionShapes/btConvexPolyhedron.cpp"
"../src/BulletCollision/CollisionShapes/btConvexInternalShape.cpp"
"../src/Bullet3Common/b3Logging.cpp"
"../src/LinearMath/btAlignedAllocator.cpp"
"../src/LinearMath/btConvexHull.cpp"
"../src/LinearMath/btConvexHullComputer.cpp"
"../src/LinearMath/btGeometryUtil.cpp"
"../src/LinearMath/btQuickprof.cpp"
"../src/LinearMath/btThreads.cpp"
"../src/Bullet3Common/b3AlignedAllocator.cpp"
"../examples/ThirdPartyLibs/glad/gl.c"
"../examples/OpenGLWindow/GLInstancingRenderer.cpp"
"../examples/OpenGLWindow/GLRenderToTexture.cpp"
"../examples/OpenGLWindow/LoadShader.cpp"
# Enabled onlu if -DBT-ENABLE-ENET is set
"../examples/ThirdPartyLibs/glad/egl.c"
"../examples/OpenGLWindow/EGLOpenGLWindow.cpp"
)

set(CXX_FLAGS "")
set(CXX_FLAGS "${CXX_FLAGS} -DGWEN_COMPILE_STATIC")
set(CXX_FLAGS "${CXX_FLAGS} -DBT_USE_DOUBLE_PRECISION")
set(CXX_FLAGS "${CXX_FLAGS} -DBT_ENABLE_ENET")
set(CXX_FLAGS "${CXX_FLAGS} -DBT_ENABLE_CLSOCKET")
set(CXX_FLAGS "${CXX_FLAGS} -DB3_DUMP_PYTHON_VERSION")
set(CXX_FLAGS "${CXX_FLAGS} -DEGL_ADD_PYTHON_INIT")
set(CXX_FLAGS "${CXX_FLAGS} -DB3_ENABLE_FILEIO_PLUGIN")
set(CXX_FLAGS "${CXX_FLAGS} -DB3_USE_ZIPFILE_FILEIO")
set(CXX_FLAGS "${CXX_FLAGS} -DBT_THREADSAFE=1")
set(CXX_FLAGS "${CXX_FLAGS} -DSTATIC_LINK_SPD_PLUGIN")
set(CXX_FLAGS "${CXX_FLAGS} -DBT_ENABLE_VHACD")


####---------WINDOWS----------###########---------WINDOWS----------########------WINDOWS---#########
set(libraries Ws2_32 Winmm User32 Opengl32 kernel32 glu32 Gdi32 Comdlg32)
set(CXX_FLAGS "${CXX_FLAGS} -DWIN32 -DGLEW_STATIC")
set(BULLET_CPP_WINDOWS_SRCS 
  "../examples/ThirdPartyLibs/enet/win32.c"
  "../examples/OpenGLWindow/Win32Window.cpp"
  "../examples/OpenGLWindow/Win32OpenGLWindow.cpp"
  "../examples/ThirdPartyLibs/glad/gl.c")
#--------------------------------------------------------------------------------------------------#


# Lets solve the issues with the normal libraries first then we can add the ${EGL_RENDERER_SOURCES}
# to the list of sources
ADD_LIBRARY(CppBullet STATIC ${CPPBULLET_SRCS}  ${BULLET_CPP_WINDOWS_SRCS})

TARGET_LINK_LIBRARIES(CppBullet ${libraries})


# INSTALL (
#     DIRECTORY ${CMAKE_SOURCE_DIR}/examples/
#     DESTINATION include/bullet
#     FILES_MATCHING PATTERN "*.h*")

INSTALL(TARGETS
  CppBullet
  LIBRARY DESTINATION lib${LIB_SUFFIX}
  ARCHIVE DESTINATION lib${LIB_SUFFIX}
)



SET_TARGET_PROPERTIES(CppBullet PROPERTIES VERSION ${CPPBULLET_VERSION})
SET_TARGET_PROPERTIES(CppBullet PROPERTIES SOVERSION ${CPPBULLET_VERSION})

