IF (PROJ_VERSION_MAJOR GREATER 5)
  MESSAGE(STATUS "Using PROJ 6 srs database.")
  SET(SRSDB srs6.db)
ELSE (PROJ_VERSION_MAJOR GREATER 5)
  MESSAGE(STATUS "Using PROJ <6 srs database.")
  SET(SRSDB srs.db)
ENDIF (PROJ_VERSION_MAJOR GREATER 5)

INSTALL(FILES ${SRSDB} DESTINATION ${QGIS_DATA_DIR}/resources RENAME srs.db)

INSTALL(FILES
              qgis.db
              symbology-style.xml
              spatialite.db
              customization.xml
              2to3migration.txt
              qgis_global_settings.ini
        DESTINATION ${QGIS_DATA_DIR}/resources)
INSTALL(DIRECTORY cpt-city-qgis-min DESTINATION ${QGIS_DATA_DIR}/resources)
INSTALL(DIRECTORY themes DESTINATION ${QGIS_DATA_DIR}/resources)
INSTALL(DIRECTORY data DESTINATION ${QGIS_DATA_DIR}/resources)
INSTALL(DIRECTORY metadata-ISO DESTINATION ${QGIS_DATA_DIR}/resources)
INSTALL(DIRECTORY palettes DESTINATION ${QGIS_DATA_DIR}/resources)
IF (HAVE_OPENCL)
INSTALL(DIRECTORY opencl_programs DESTINATION ${QGIS_DATA_DIR}/resources)
ENDIF (HAVE_OPENCL)

IF (WITH_SERVER)
        INSTALL(DIRECTORY server DESTINATION ${QGIS_DATA_DIR}/resources)
ENDIF (WITH_SERVER)

IF (APPLE)
  # ASN.1 definition files of PKIX elements
  INSTALL(FILES pkcs8.asn
          DESTINATION ${QGIS_DATA_DIR}/resources)
ENDIF (APPLE)
