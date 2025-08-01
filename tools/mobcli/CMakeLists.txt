set(CMAKE_CXX_STANDARD 17)
set(MOBILUS_CA_FILE "${PROJECT_SOURCE_DIR}/certs/mobilelabs_mobilus_ca.crt")

configure_file(
  include/config.h.in
  "${CMAKE_CURRENT_BINARY_DIR}/include/config.h"
  @ONLY
)

add_executable(mobcli
  src/main.cpp
  src/App.cpp
  src/commands/CommonCommand.cpp
  src/commands/CallEventsCommand.cpp
  src/commands/CurrentStateCommand.cpp
  src/commands/DeviceListCommand.cpp
  src/commands/DeviceSettingsCommand.cpp
  src/commands/NetworkSettingsCommand.cpp
  src/commands/SessionCommand.cpp
  src/commands/SubscribeCommand.cpp
)

target_include_directories(mobcli 
  PRIVATE
    src
    include
    ${CMAKE_CURRENT_BINARY_DIR}/include
)

target_link_libraries(mobcli
  PRIVATE
    mobilus_gtw_client
)
