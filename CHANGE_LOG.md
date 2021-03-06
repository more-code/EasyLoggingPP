CHANGE LOG - EasyLogging++
--------------------------

Change log was not kept before version 2.1.

#### 7.xx
 * 7.00:
    - Completely re-written with focus on performance and usability improvements (issue #27)
    - Code:
       - C++98 to support old applications as well
       - Now make full use of STL for performance improvement
       - New namespace easyloggingpp::internal::helper for internal use instead of C-like functions
       - Uses custom embedded mutex so does not have to worry about libraries availability (issue #28)
       - New reuseable macros 
    - New features:
       - New log types
          - `BINFO`, `BWARNING` ... etc, business loggers
          - `SINFO`, `SWARNING` ... etc, security loggers
          - `PINFO`, `PWARNING` ... etc, performance loggers
       - Inject new log types as per your requirements 
       - Added `easyloggingpp::VersionInfo` with formatted displayable information
    - Removed:
       - PERFORMANCE as severity level instead added it as log type with `PINFO << log;` or `PDEBUG << log` etc
       - Performance tracking disables with debug logs
       - _END_EASYLOGGINGPP is not needed anymore, everything is handled internally 
    - Improvements:
       - Now you dont need `_END_EASYLOGGINGPP` and dont need to worry about memory leaks, everything is done internally
       - Improved web page (icplusplus.com/tools/easylogging/)
    - Github issues closed:
       - Issue #27 Re-write whole code to improve performance
       - Issue #14 Make debug logs really when debugging
       - Issue #5 Test in win machine
       - Issue #28 Embed custom mutex class
       - Issue #29 Ability to inject new logger types
       - Issue #30 Introduce log types for type of logger 
       - Issue #31 Ditch PERFORMANCE as severity level, add it as log type
    - Licence: Changed to open source licence with full details within header

 * 7.01: Provides safe interface to use Register template outside EasyLogging++
 * 7.20: Performance tracking now tracks upto milliseconds
 * 7.21: Performance tracking is now exact not approx so got rid of ~ char
 * 7.22: Minor refactoring
 * 7.25:
     - Updated default log formats to make logs more easy to read
     - Fixed bug from 7.22
 * 7.26:
     - Updated default log format to align to make log easy to read, these log formats can be customized as per requirments
     - Updated log types format-output to prevent confusion with severity level
     - Single format specifier per severity level for performance improvement and error preventions.
 * 7.27:
     - Ability to check log counter position by introducing `_ELPP_COUNTER_POSITION`
     - Counter now gets reset every 100,000 instead of 5000 iterations.
 * 7.28: Fix date issue on RHEL for applications using Qt
 * 7.30:
      - Support for QString and other Qt based classes (QBool, qint*, QChar ...) *Container not supported as of yet*
      - Qt based classes have to be used with `_ELPP_EXPERIMENTAL`
 * 7.31:
      - Format source code
      - Standard vector (std::vector) for std::string and other primitive data types
 * 7.32:
      - Standard vector to support third party libraries if using, see sample for details (samples/container_log.cpp)
      - Primitive bool now logs true/false instead of 1/0
      - Container logs wraps quotes around each element
 * 7.33:
      - Support for std::list log
      - Fixed issue with post-include for QString
 * 7.35:
      - Support for `std::pair`, `std::map`, Qt based containers and `QPair`
      - Changed `_DO_NOT_SUPPORT_CPP_LIBRARIES` to `_DISABLE_CPP_THIRD_PARTY_LIBRARIES_LOGGING`
      - Introduced `_DISABLE_CPP_LIBRARIES_LOGGING` to disable containers and other classes logging support
 * 7.36: Raw array logging
 * 7.37: Support for container (vector, list) of pointers
 * 7.38: Fix for overloaded const containers
 * 7.39: No support for raw arrays any more instead support for pointer
 * 7.40: Disable performance tracking using `_ENABLE_PERFORMANCE_TRACKING`
 * 7.41: Major improvements around logging pointers and code clean up around containers
 * 7.42: Configurable severity type for performance tracking
 * 7.43: Improved comments
 * 7.45: Fixed all issues on windows (Visual C++ 8.0, 9.0, 10.0, 11.0)
 * 7.50:
      - Massive performance improvements by setting formats at initialize time
      - Introduced MILLISECONDS_LENGTH for UNIX
 * 7.55:
      - Improved multi-threading
      - Dropped support for power PC
      - Prevent potential naming conflicts with classes
      - Removed `using namespace` and naming explicitly
      - Better format by introducing internal::constants
 * 7.56: Simplified readibility

#### 6.xx
 * 6.00:
    - Changed the way of logging i.e, no parentheses required anymore (issue #26)
    - Naming conflicts for debug logs (issue #25)
    - Old names still supported with `_SUPPORT)_LEGACY_LOG_NAMES` macro (issue #25)
    - Removed STATUS and HINT log levels (issue #23)
    - Now supports full version only - linked version is ditched away (issue #24)
 * 6.01: Fixes from 6.00 changes
 * 6.02: Format update to simplify readibility
 * 6.03: Fixed memory leak from END_MAIN(..) while using performance tracker
 * 6.04: Failure fix when performance log is disabled
 * 6.10:
    - Revision 1.2 for unit tests
    - Fix some issues found by rev1.2 tests

#### 5.0
 * 5.00:
    - Support for multithreaded applications for C++0X / C++11 (issue #21)
    - Fixed up issue with `_ALWAYS_CLEAN_LOGS` (issue #22)
    - Fixed up bug with interval log where it was off by 1
    - Extended for linked and full type (see README at github for details)
 * 5.01: Fixed up compile failure if logs disabled for both linked and full
 * 5.02: Minor comment fixes for readibility
 * 5.03: Fixed bug with `_DISABLE_MUTEX`
 * 5.04: Date/time fix for windows (issue #4)
 * 5.05: Use QMutex when available
 * 5.06: Macro rename for mutex evaluation

#### 4.xx
 * 4.00:
    - Major improvement for multiple files project
    - Introduced `INITIALIZE_EASYLOGGINGPP`
 * 4.01:
    - Added inline doc
    - Fix issue with `TO_STANDARD_OUTPUT` segmentation fault
    - Added support for `--verbose` for level 9
 * 4.02: Minor naming fixes (refactoring)
 * 4.03: Added extra namespace to suppress `unused` warnings
 * 4.04:
    - Performance improvement when determining log format
    - Performance improvement for escape character in log format
 * 4.05: Performance improvement while building path
 * 4.06: Minor namespace fix
 * 4.07: Introduced `LOG_EVERY_N` (interval logging) for all log levels
 * 4.08:
    - Interval logging works well even in the same iteration
    - Introduced `::easyloggingpp::version` namespace for version info of current version
 * 4.09: Minor issue fix regarding multiple-definition error
 * 4.10: gcc warnings
 * 4.11: Registered counters lookup improvement
 * 4.12: Fully qualified names used
 * 4.13: Added partial compiler evaluation macros
 * 4.14: Return on first error while creating log path
 * 4.15: END_FUNC with return value now

#### 3.3
 * 3.30:
    - Added new `QA(..)` logs (issue #17)
    - Splits functions into namespaces (issue #18)
    - Fixed issue with helper functions when logs disabled
    - Fixed issue with compiling using LLVM on mac (issue #16)
 * 3.31: Fixes issue with `const char**` vs `char**` argv (issue #19)
 * 3.32: Tries harder (using `hostname`) to retrieve host name on ubuntu based linux.
 * 3.33: Fixed releaseMemory
 * 3.34: Type check for verbose log argument
 * 3.35: Memory leak issue when tracking performance (issue #20)
 * 3.36: Introduced MAIN, END_MAIN and RETURN_MAIN for memory release safety

#### 3.2
 * 3.20: Added conditional logging using `INFO_IF`, `DEBUG_IF`, etc.
 * 3.21: Code readibility improvements
 * 3.22: Introduced VERBOSE logging
 * 3.23: Simplified for new logs by creating LogType class
 * 3.24: Make sure `%vlevel` is only applicable to VERBOSE logs
 * 3.25: Minor improvements
 * 3.26: Minor improvements
 * 3.27: Fixed issue #15
 * 3.28: Fix for VERBOSE_IF
 * 3.29: Introduced `_END_EASYLOGGINGPP` to make valgrind happy
 
#### 3.1
 * 3.10: Removed comments around configuration to point to README
 * 3.11: Type / level constructor called within WRITE_LOG macro only 
 * 3.12: minor fixes around comments
 * 3.13: fixes for update.sh
 * 3.14: fix for windows compile failure, thanks to `codyzu`
 * 3.15: 
    - Added more control over disabling logs
    - Changed from `_DISABLE_EASYLOGGINGPP` to `_DISABLE_LOGS`
 * 3.16: Minor improvement
 * 3.17: Minor logic improvement
 * 3.18: Added support for regression testing to clean log every time you run application.
 * 3.19: Added escape character for log format

#### 3.0
 * Major improvements
 * Added format specifiers for each logging level
 * Issue#7 formatting logs
 * 3.01: Fix up path creation on mac
 * 3.02: Added slash as escape character in format
 * 3.03: Fixed bug for other OS than mac, linux or windows
 * 3.04: Got rid of new line character `%n` instead `\n` can be used
 * 3.05 and 3.06: Fixes for \n from 3.04
 * 3.07: Adds _DISABLE_EASYLOGGINGPP, macro to disable EasyLogging++ while compiling
 * 3.08: Fix for update.sh includes
 * 3.09 improvements around log file performance

#### 2.8
 * Added `update.sh` to update your old easylogging++.h without losing configuration
 * A lot of date improvements in terms of memory and performance efficiency
 * 2.843: Fixes milliseconds issue for linux only.
 * 2.844: Do not calculate milliseconds when SHOW_TIME is set to false
 * 2.845: Strict support for any other OS than linux or windows

#### 2.7
 * Fixed up log path creation issue to create whole path

#### 2.6
 * Added helper function `string readLog(void)`
 * Changed `WARN` to `WARNING` for warning logs

#### 2.5
 * Added _WIN64 macro checks for 64-bit windows machines
 * Issue#3 Force log file creation
 * Memory efficient approaches for writing logs

#### 2.3
 * Added host and username to be included in logs
 * Added `release.sh` for easy releaases

#### 2.2
 * Added PERFORMANCE, STATUS and HINTS logging levels

#### 2.1
 * Fixed time issues
