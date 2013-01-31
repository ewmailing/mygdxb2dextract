set(Box2Dgdx_source
	com.badlogic.gdx.math.Matrix4.h
	com.badlogic.gdx.math.Matrix4.cpp
	com.badlogic.gdx.physics.box2d.Body.cpp
	com.badlogic.gdx.physics.box2d.Body.h
	com.badlogic.gdx.physics.box2d.ChainShape.cpp
	com.badlogic.gdx.physics.box2d.ChainShape.h
	com.badlogic.gdx.physics.box2d.CircleShape.cpp
	com.badlogic.gdx.physics.box2d.CircleShape.h
	com.badlogic.gdx.physics.box2d.Contact.cpp
	com.badlogic.gdx.physics.box2d.Contact.h
	com.badlogic.gdx.physics.box2d.ContactImpulse.cpp
	com.badlogic.gdx.physics.box2d.ContactImpulse.h
	com.badlogic.gdx.physics.box2d.EdgeShape.cpp
	com.badlogic.gdx.physics.box2d.EdgeShape.h
	com.badlogic.gdx.physics.box2d.Fixture.cpp
	com.badlogic.gdx.physics.box2d.Fixture.h
	com.badlogic.gdx.physics.box2d.Joint.cpp
	com.badlogic.gdx.physics.box2d.Joint.h
	com.badlogic.gdx.physics.box2d.Manifold.cpp
	com.badlogic.gdx.physics.box2d.Manifold.h
	com.badlogic.gdx.physics.box2d.PolygonShape.cpp
	com.badlogic.gdx.physics.box2d.PolygonShape.h
	com.badlogic.gdx.physics.box2d.Shape.cpp
	com.badlogic.gdx.physics.box2d.Shape.h
	com.badlogic.gdx.physics.box2d.World.cpp
	com.badlogic.gdx.physics.box2d.World.h
	com.badlogic.gdx.physics.box2d.joints.DistanceJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.DistanceJoint.h
	com.badlogic.gdx.physics.box2d.joints.FrictionJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.FrictionJoint.h
	com.badlogic.gdx.physics.box2d.joints.GearJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.GearJoint.h
	com.badlogic.gdx.physics.box2d.joints.MouseJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.MouseJoint.h
	com.badlogic.gdx.physics.box2d.joints.PrismaticJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.PrismaticJoint.h
	com.badlogic.gdx.physics.box2d.joints.PulleyJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.PulleyJoint.h
	com.badlogic.gdx.physics.box2d.joints.RevoluteJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.RevoluteJoint.h
	com.badlogic.gdx.physics.box2d.joints.RopeJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.RopeJoint.h
	com.badlogic.gdx.physics.box2d.joints.WeldJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.WeldJoint.h
	com.badlogic.gdx.physics.box2d.joints.WheelJoint.cpp
	com.badlogic.gdx.physics.box2d.joints.WheelJoint.h
)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR} ${BOX2D_INCLUDE_DIR})

if(BOX2DGDX_BUILD_SHARED)
	add_library(Box2Dgdx_shared SHARED
		${Box2Dgdx_source}
	)
	TARGET_LINK_LIBRARIES(Box2Dgdx_shared ${BOX2D_LIBRARY})
	SET_TARGET_PROPERTIES(Box2Dgdx_shared PROPERTIES OUTPUT_NAME "Box2Dgdx")
endif()


if(BOX2DGDX_BUILD_STATIC)
	add_library(Box2Dgdx_static STATIC
		${Box2Dgdx_source}
	)
	SET_TARGET_PROPERTIES(Box2Dgdx_static PROPERTIES OUTPUT_NAME "Box2Dgdx")
endif()

if(BOX2DGDX_INSTALL)
	# install libraries
	if(BOX2D_BUILD_SHARED)
		install(TARGETS Box2Dgdx_shared EXPORT Box2Dgdx-targets DESTINATION lib)
	endif()
	if(BOX2D_BUILD_STATIC)
		install(TARGETS Box2Dgdx_static EXPORT Box2Dgdx-targets DESTINATION lib)
	endif()

	# install build system hooks for third-party apps
endif()

