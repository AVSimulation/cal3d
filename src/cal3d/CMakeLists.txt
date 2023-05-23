set(TARGET_NAME cal3d)

set(SOURCE_FILES
animation.cpp
animation_action.cpp
animation_cycle.cpp
bone.cpp
buffersource.cpp
cal3d_wrapper.cpp
calxmlbindings.cpp
coreanimatedmorph.cpp
coreanimation.cpp
corebone.cpp
corekeyframe.cpp
corematerial.cpp
coremesh.cpp
coremodel.cpp
coremorphkeyframe.cpp
coremorphtrack.cpp
coreskeleton.cpp
coresubmesh.cpp
coresubmorphtarget.cpp
coretrack.cpp
dualquaternion.cpp
error.cpp
global.cpp
hardwaremodel.cpp
loader.cpp
matrix.cpp
mesh.cpp
mixer.cpp
model.cpp
morphtargetmixer.cpp
physique.cpp
physiquedualquaternion.cpp
platform.cpp
quaternion.cpp
renderer.cpp
saver.cpp
skeleton.cpp
springsystem.cpp
streamsource.cpp
submesh.cpp
tinybind.cpp
tinyxml.cpp
tinyxmlerror.cpp
tinyxmlparser.cpp
vector.cpp
xmlformat.cpp
)

SET(HEADER_FILES
animation.h
animation_action.h
animation_cycle.h
animcallback.h
bone.h
buffersource.h
cal3d.h
cal3d_wrapper.h
calxmlbindings.h
coreanimatedmorph.h
coreanimation.h
corebone.h
corekeyframe.h
corematerial.h
coremesh.h
coremodel.h
coremorphkeyframe.h
coremorphtrack.h
coreskeleton.h
coresubmesh.h
coresubmorphtarget.h
coretrack.h
datasource.h
dualquaternion.h
error.h
global.h
hardwaremodel.h
loader.h
matrix.h
mesh.h
mixer.h
model.h
morphtargetmixer.h
physique.h
physiquedualquaternion.h
platform.h
quaternion.h
refcounted.h
refptr.h
renderer.h
resource.h
saver.h
skeleton.h
springsystem.h
streamsource.h
submesh.h
tinybind.h
tinyxml.h
transform.h
vector.h
xmlformat.h
)

SET(RESOURCE_FILES
cal3d.rc
)

add_library(${TARGET_NAME} SHARED
${SOURCE_FILES}
${HEADER_FILES}
${RESOURCE_FILES}
)

target_include_directories(${TARGET_NAME}
PRIVATE
${CMAKE_CURRENT_SOURCE_DIR}/..
)

target_compile_definitions(${TARGET_NAME} PRIVATE CAL3D_EXPORTS)

SET(INSTALL_INCDIR include)
SET(INSTALL_BINDIR bin)
IF(WIN32)
    SET(INSTALL_LIBDIR bin)
    SET(INSTALL_ARCHIVEDIR lib)
ELSE()
    SET(INSTALL_LIBDIR lib)
    SET(INSTALL_ARCHIVEDIR lib)
ENDIF()

INSTALL(
    TARGETS ${TARGET_NAME}
    # EXPORT osg-targets
    RUNTIME DESTINATION ${INSTALL_BINDIR} COMPONENT cal3d
    LIBRARY DESTINATION ${INSTALL_LIBDIR} COMPONENT cal3d
    ARCHIVE DESTINATION ${INSTALL_ARCHIVEDIR} COMPONENT cal3d-dev
)

INSTALL (
    FILES ${HEADER_FILES}
    DESTINATION ${INSTALL_INCDIR}/${TARGET_NAME}
    COMPONENT cal3d-dev
)
