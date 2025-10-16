This document provides comprehensive documentation for all Python files in the 100daysofpyats project, organized by directory and explained with their purpose and functionality.

## Project Overview
This is a learning project focused on pyATS (Python Automated Test Systems), covering various aspects of network automation, testing, and configuration management over different days of study.

## Credits and Attribution
This project contains code from multiple sources and authors we have used to test our comprehension of the book :
- Original learning scripts and examples developed during the 100daysofpyats journey
- Cisco Systems pyATS example scripts by Wei Chen
- bubo project by John Capobianco (2022)
- Various community contributions and examples

---

## Day 7-11: Basic Test Scripts

### `day7_11/my_testscript.py`
**Purpose**: Basic pyATS test script demonstrating fundamental concepts

**Functionality**:
- **CommonSetup**: Establishes connection to IOS-XR device named 'DEMO'
- **PingTestcase**: Performs ping tests to multiple destinations (10.0.101.1, 10.0.102.2)
- **Ping Logic**: Uses regex to extract success rate from ping results
- **Error Handling**: Graceful failure handling with detailed error messages
- **CommonCleanup**: Disconnects from devices after testing

**Key Features**:
- Loop decorator for testing multiple destinations
- Regex pattern matching for result parsing
- Proper connection lifecycle management

### `day7_11/my_testscript2.py`
**Purpose**: Simplified test script for interface status checking

**Functionality**:
- **Device Connection**: Connects to 'DEMO' device from testbed
- **Interface Parsing**: Uses `show ip interface brief` command parsing
- **Interface Status Check**: Iterates through interfaces and checks protocol status
- **Status Reporting**: Prints status of each interface (up/down)

**Key Features**:
- Direct testbed loading from YAML file
- Interface status validation
- Simple print-based reporting

---

## Day 12-16: Parsers and Data Extraction

### `day12_16/my_parser.py`
**Purpose**: Basic command parsing demonstration

**Functionality**:
- **Testbed Loading**: Loads device configuration from testbed.yaml
- **Command Parsing**: Parses `show version` and `show ip interface brief`
- **Data Iteration**: Loops through parsed interface data
- **Output Display**: Prints interface information

**Key Features**:
- Basic pyATS parsing capabilities
- Simple data structure navigation
- Clean connection management

### `day12_16/my_parser2.py`
**Purpose**: Enhanced parser with conditional logic

**Functionality**:
- **Version Extraction**: Extracts and displays software version from device
- **Interface Filtering**: Shows only interfaces that are operationally up
- **Status Validation**: Checks both interface_status and protocol_status
- **Formatted Output**: Professional output formatting with separators

**Key Features**:
- Advanced data filtering
- Conditional interface status checking
- Professional output formatting

---

## Day 17-22: Test-Driven Development and Intent-Based Testing

### `day17_22/my_tdd.py`
**Purpose**: Test-driven development approach for network configuration

**Functionality**:
- **Interface Validation**: Tests for interface existence and configuration
- **Loopback Testing**: Specific tests for Loopback120 interface
- **Configuration Management**: Configures missing interfaces during testing
- **Pre/Post Validation**: Tests before and after configuration changes

**Key Features**:
- TDD methodology implementation
- Dynamic configuration based on test results
- Interface lifecycle testing

### `day17_22/my_tdd2.py`
**Purpose**: Advanced TDD with comprehensive interface testing

**Functionality**:
- **Interface Learning**: Uses pyATS learn functionality for interface data
- **Error Counter Testing**: Tests for input errors, CRC errors, output errors
- **Duplex Mode Validation**: Ensures interfaces are in full duplex mode
- **Operational Status Check**: Validates interface operational state
- **Threshold-Based Testing**: Uses configurable thresholds for error validation

**Key Features**:
- Counter-based validation
- Duplex mode checking
- Reusable test helper methods
- Error threshold management

### `day17_22/bubo_SSH.py`
**Purpose**: Intent-based testing using SSH connections

**Functionality**:
- **Intent Validation**: Compares actual configuration against intended state
- **Domain Name Testing**: Validates IP domain name configuration
- **Interface Intent**: Ensures configured interfaces match intent model
- **Configuration Remediation**: Automatically fixes misconfigurations
- **Pre/Post Comparison**: Shows differences before and after changes

**Key Features**:
- Intent-based network testing
- Automated configuration remediation
- Comprehensive interface validation
- Tabular result reporting

### `day17_22/bubo/` Directory Files

#### `bubo/bubo_REST.py`
**Purpose**: REST API-based intent testing using RESTCONF

**Functionality**:
- **RESTCONF Integration**: Uses Cisco IOS-XE Native and OpenConfig YANG models
- **MOTD Banner Testing**: Validates message of the day configuration
- **Domain Name Validation**: REST-based domain name configuration testing
- **Interface Management**: Creates and validates interfaces via REST API
- **Error Counter Analysis**: Comprehensive interface error monitoring

**Key Features**:
- RESTCONF/YANG model integration
- REST API configuration updates
- OpenConfig standard compliance
- Real-time configuration validation

#### `bubo/bubo_SSH.py`
**Purpose**: SSH-based version of intent testing (simplified)

**Functionality**:
- **SSH Configuration**: Uses traditional SSH for device interaction
- **Intent Comparison**: Validates configuration against intent files
- **Interface Testing**: Comprehensive interface error and status checking
- **Configuration Updates**: SSH-based configuration remediation

**Key Features**:
- Traditional SSH approach
- Intent-driven testing
- Interface health monitoring
- Configuration synchronization

#### `bubo/bubo_REST_job.py` & `bubo/bubo_SSH_job.py`
**Purpose**: Job files to execute the respective test scripts

**Functionality**:
- **Runtime Management**: Handles testbed loading and script execution
- **Testbed Selection**: Uses appropriate testbed files for REST/SSH testing
- **Script Orchestration**: Executes corresponding test scripts with proper parameters

---

## Day 23-27: Automated Documentation Generation

### `day23_27/auto_docs.py`
**Purpose**: Comprehensive network documentation automation

**Functionality**:
- **Multi-format Output**: Generates JSON, YAML, CSV, Markdown, HTML documentation
- **Mermaid Diagrams**: Creates various Mermaid diagram types (flowchart, class, state, entity-relationship, mind map)
- **Template-based Generation**: Uses Jinja2 templates for flexible output formatting
- **Interface Documentation**: Focuses on interface brief information parsing

**Test Cases**:
1. **JSON Export**: Saves interface data as JSON files
2. **YAML Export**: Converts interface data to YAML format
3. **CSV Export**: Tabular data export using Jinja2 templates
4. **Markdown Tables**: Professional documentation tables
5. **Mermaid Diagrams**: Multiple diagram types for visualization
6. **HTML Reports**: Web-ready documentation

**Key Features**:
- Template-driven documentation
- Multiple output formats
- Automated report generation
- Diagram creation capabilities

### `day23_27/auto_docs_job.py`
**Purpose**: Job orchestration for documentation generation

**Functionality**:
- **Testbed Management**: Handles testbed file loading
- **Script Execution**: Runs the auto_docs.py test script
- **Runtime Configuration**: Manages execution parameters

---

## Day 28-32: Network Testing and Monitoring

### `day28_32/version_testing.py`
**Purpose**: Device version validation and threshold testing

**Functionality**:
- **Version Parsing**: Extracts software versions from devices
- **Threshold Comparison**: Validates versions against minimum requirements
- **Multi-Platform Support**: Handles IOS and ASA device types
- **Rich Table Output**: Professional tabular display of results
- **JSON Export**: Saves version data for reporting

**Key Features**:
- Version threshold enforcement
- Multi-platform device support
- Rich console output formatting
- Automated compliance checking

### `day28_32/bgp_test.py`
**Purpose**: BGP protocol testing and validation

**Functionality**:
- **BGP Neighbor Testing**: Validates established BGP sessions
- **Route Table Analysis**: Checks for specific BGP routes
- **Interface Manipulation**: Tests BGP behavior during interface shutdowns
- **Recovery Testing**: Validates BGP recovery after interface restoration
- **State Comparison**: Compares pre/post test BGP states

**Key Features**:
- BGP session monitoring
- Route presence validation
- Network resilience testing
- Automated recovery verification

### `day28_32/ospf_test.py`
**Purpose**: OSPF protocol testing and validation

**Functionality**:
- **OSPF Neighbor Discovery**: Validates OSPF neighbor relationships
- **Interface Testing**: Tests OSPF behavior during interface changes
- **Route Validation**: Checks for OSPF routes in routing table
- **Recovery Testing**: Validates OSPF convergence after interface restoration

**Key Features**:
- OSPF neighbor state monitoring
- Network convergence testing
- Route table validation
- Protocol resilience testing

### `day28_32/net_reach.py`
**Purpose**: Network reachability and latency testing

**Functionality**:
- **Ping Testing**: Tests connectivity to external destinations (9.9.9.9)
- **Success Rate Analysis**: Validates 100% ping success rate
- **Latency Monitoring**: Tests average latency against thresholds
- **Rich Reporting**: Professional table output for results
- **JSON Export**: Saves reachability data for analysis

**Key Features**:
- Network connectivity validation
- Latency threshold monitoring
- Success rate analysis
- Professional reporting

### Job Files (`*_job.py`)
All job files in this directory follow the same pattern:
- **Testbed Loading**: Handles testbed configuration loading
- **Script Execution**: Orchestrates test script execution
- **Runtime Management**: Manages execution parameters and file paths

---

## Day 33-37: Genie Harness and Triggers

### `day33_37/custom_trig.py`
**Purpose**: Custom trigger implementation for OSPF testing

**Functionality**:
- **Custom Trigger Class**: Implements MyShutNoShutOspf trigger
- **OSPF Validation**: Checks OSPF configuration and status
- **Process Manipulation**: Shuts down and restarts OSPF processes
- **State Verification**: Validates OSPF process states before/after changes

**Key Features**:
- Custom trigger development
- OSPF process lifecycle management
- Automated validation steps
- Error handling and skipping logic

### Genie Harness Files (`GH*.py`)

#### `day33_37/GH.py`
**Purpose**: Basic Genie harness usage

**Functionality**:
- **Built-in Triggers**: Uses TriggerSleep for demonstration
- **Built-in Verifications**: Uses Verify_IpInterfaceBrief
- **PTS Features**: Demonstrates Profile Test Suite with interface features

#### `day33_37/GH2.py`
**Purpose**: Verification-focused Genie testing

**Functionality**:
- **Multiple Verifications**: Uses Verify_Interfaces and Verify_Bgp
- **External Datafiles**: Utilizes external verification configuration

#### `day33_37/GH3.py`
**Purpose**: Custom trigger execution

**Functionality**:
- **Custom Trigger**: Executes TriggerMyShutNoShutOspf
- **External Configuration**: Uses trigger_datafile for configuration

#### `day33_37/GH4.py`
**Purpose**: Combined trigger and verification testing

**Functionality**:
- **Trigger Execution**: Custom OSPF trigger with external configuration
- **Verification**: OSPF database router verification
- **Multiple Datafiles**: Uses separate configuration files for triggers and verifications

#### `day33_37/GH5.py`
**Purpose**: pyATS integration with Genie standalone

**Functionality**:
- **GenieStandalone Class**: Integrates Genie with pyATS test structure
- **Combined Testing**: Executes triggers and verifications within pyATS sections
- **UUT Definition**: Specifies unit under test for focused testing

### `day33_37/GH5_job.py`
**Purpose**: Job orchestration for GH5 testing

---

## Day 38-42: Configuration Generation

### `day38_42/gen_conf_genie.py`
**Purpose**: Configuration generation using Genie configuration objects

**Functionality**:
- **Interface Object Creation**: Creates GigabitEthernet4 interface object
- **IP Configuration**: Sets IPv4 address and netmask
- **Interface State**: Configures interface as no shutdown
- **Config Generation**: Builds configuration without applying to device

**Key Features**:
- Object-oriented configuration approach
- Configuration preview capability
- Structured interface configuration

### `day38_42/gen_conf_jinja2.py`
**Purpose**: Configuration generation using Jinja2 templates

**Functionality**:
- **Template Loading**: Uses Jinja2 template for logging configuration
- **Variable Substitution**: Passes host list for template rendering
- **Config Rendering**: Generates configuration from templates

**Key Features**:
- Template-based configuration generation
- Variable parameterization
- Flexible configuration templating

---

## pyATS iOS Sample

### `pyats-ios-sample/pyats_ios_example.py`
**Purpose**: Comprehensive pyATS demonstration script

**Functionality**:
- **Topology Validation**: Ensures proper testbed configuration
- **Device Connections**: Establishes connections to multiple iOS devices
- **Interface Counting**: Validates interface counts between commands
- **Ping Testing**: Performs connectivity tests between devices
- **Command Parsing**: Demonstrates show version and show ip interface brief parsing

**Key Features**:
- Complete pyATS workflow demonstration
- Multi-device testing
- Interface validation
- Comprehensive error handling
- Professional documentation

### `pyats-ios-sample/pyats_ios_example_job.py`
**Purpose**: Job file for iOS example execution

**Functionality**:
- **Argument Parsing**: Handles device name customization
- **Script Orchestration**: Executes the main example script
- **Path Management**: Handles script location resolution

---

## Key Technologies and Concepts Used

### pyATS Framework
- **aetest**: Automated Easy Testing framework
- **Device Connection**: Automated device connectivity management
- **Command Parsing**: Structured data extraction from CLI commands
- **Test Orchestration**: Test case organization and execution

### Genie Framework
- **Learn**: Device state learning and modeling
- **Parse**: Command output parsing and structuring
- **Harness**: Test automation and orchestration
- **Triggers**: Network state manipulation testing
- **Verifications**: Network state validation

### Network Protocols Tested
- **BGP**: Border Gateway Protocol session and routing validation
- **OSPF**: Open Shortest Path First protocol testing
- **Interface Management**: Layer 2/3 interface configuration and monitoring

### Output Formats
- **JSON**: Structured data export
- **YAML**: Human-readable configuration format
- **CSV**: Tabular data export
- **Markdown**: Documentation generation
- **HTML**: Web-ready reports
- **Mermaid Diagrams**: Visual network documentation

### Testing Methodologies
- **TDD**: Test-Driven Development for network configuration
- **Intent-Based Testing**: Configuration validation against intended state
- **Threshold Testing**: Performance and error rate validation
- **Resilience Testing**: Network protocol recovery validation

