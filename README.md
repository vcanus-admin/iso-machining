# ISO - Machining Process

## Machining Project
 - String id
 - WorkPlan mainWorkPlan
 - List<String> workpieceIds
 - Person owner
 - List<Revision> revision
  
## Executable
 - String id
 `
 	enum E_EXECUTABLE_TYPE
	{
		UNDEFINED_TYPE				= 0x00000000,
		WORKINGSTEP					= 0x10000000,
		NC_FUNCTION					= 0x01000000,
		PROGRAM_STRUCTURE			= 0x00100000,

		MACHINING_WORKINGSTEP		= 0x11000000,
		RAPID_MOVEMENT				= 0x10100000,
		TOUCH_PROBING				= 0x10010000,
	};
  `
## Workplan extends Executable
 - Map<String, Executable> elements
 - Executable currentElement
 - Setup setup
 - ProcessGeometry effect
 - Map<String,int> memberStringTable;
 `
 	enum enum_member_string_table
	{
		E_STR_ITS_ELEMENTS=0,
		E_STR_ITS_SETUP,
		E_STR_ITS_EFFECT,
		E_STR_ITS_CURRENT_ELEMENT,
		E_STR_MEMBER_SIZE
	};
 `
 
 
## Operation
 `
 //	enum E_OPERATION_TYPE
//	{
//		UNDEFINED_OPERATION		= 000000000000,
//
//		MACHINING_OPERATION		= 010000000000,
//		RAPID_MOVEMENT			= 001000000000,
//		TOUCH_PROVING			= 000100000000,
//
//		// MACHINING OPERATION ===============
//		MILLING_MACHINING		= 011000000000,
//		TURNING_MACHINING		= 010100000000,
//		// MACHINING OPERATION ===============
//
//		// MILLING MACHINING =================
//		MILLING_TYPE			= 011100000000,
//		FREEFORM_OPERATION		= 011110000000, 
//		TWO5D_MILLING_OPERATION	= 011101000000,
//
//		DRILLING_TYPE			= 011010000000,
//		DRILLING_OPERATION		= 011011000000, 
//		BORING_OPERATION		= 011010100000, 
//		BACK_BORING				= 011010010000, 
//		TAPPING					= 011010001000, 
//		THREAD_DRILLING			= 011010000100,
//		// MILLING MACHINING =================
//
//		// TURNING MACHINING =================
//		FACING					= 010110000000, 
//		GROOVING				= 010101000000, 
//		CONTOURING				= 010100100000, 
//		THREADING				= 010100010000, 
//		KNURLING				= 010100001000
//		// TURNING MACHINING =================
//	};
 `

## Technology extends ProcessData
  - Double feedrate
  - Integer feedrateReference
`
	enum E_TECHNOLOGY_TYPE
	{
		UNDEFINED_TECHNOLOGY		= 0, //0x00000000,

		MILLING_TECHNOLOGY			= 10000, //0x00000001,
		TURNING_TECHNOLOGY			= 20000, //0x00000010,
	};

	enum E_TOOL_REFERENCE_POINT //tool_reference_point
	{
     TCP,
     CCP
	};
`
### MillingTechnology extends Technology
 - Double rotationSpeed
 - Double speed
 - Double maxSpeed
 
### TurningTechnology extends Technology
 - SpeedSelect spindleSpeed
 - Double feedPerRevolution
 - Boolean syncSpindleAndZFeed
 - Boolean inhibitFeedrateOverride
 - Boolean inhibitSpindleOverride
 
 

 - machining operation
 - machining feature
 - tool
 - material side and feed direction ?
 
### Tool
 - toolbody
   - twist drill
   - 
   
#### Placement
 - CartesianPoint location
 
## MachineFunctions

### TurningMachineFunctions extends MachineFunctions

## ApproachRetractStrategy

### TurningApproachRetractStrategy extends ApproachRetractStrategy

### MachiningOperation extends Operation
 - String id
 - Double retractPlane
 - CartesianPoint cutStartPoint
 - String tool
 - MachiningStrategy machiningStrategy
 - Technology technology
 - MachineFunction machineFunction
 `
 enum E_MACHINING_OPERATION_TYPE
	{
		//UNDEFINED_OPERATION		= 0x00000000,

		//// MACHINING OPERATION ===============
		//MILLING_MACHINING		= 0x10000000,
		//TURNING_MACHINING		= 0x01000000,
		//// MACHINING OPERATION ===============

		//// MILLING MACHINING =================
		//MILLING_TYPE			= 0x11000000,
		//FREEFORM_OPERATION		= 0x11100000, 
		//TWO5D_MILLING_OPERATION	= 0x11010000,

		//// DRILLING TYPE
		//DRILLING_TYPE			= 0x10100000,

		//DRILLING_OPERATION		= 0x10110000, 
		//// DRILLING_TYPE -> DRILLING_OPERATION
		//DRILLING				= 0x10111000,
		//CENTER_DRILLING			= 0x10110100,
		//COUNTER_SINKING			= 0x10110010,
		//MULTISTEP_DRILLING		= 0x10110001,

		//BORING_OPERATION		= 0x10101000, 
		//BACK_BORING				= 0x10100100, 
		//TAPPING					= 0x10100010, 
		//THREAD_DRILLING			= 0x10100001,
		//// MILLING MACHINING =================

		//// TURNING MACHINING =================
		//FACING					= 0x01100000,
		//FACING_ROUGH			= 0x01110000,
		//FACING_FINISH			= 0x01101000,
		//GROOVING				= 0x01010000,
		//GROOVING_ROUGH			= 0x01011000,
		//GROOVING_FINISH			= 0x01010100,
		//CONTOURING				= 0x01001000,
		//CONTOURING_ROUGH		= 0x01001100, 
		//CONTOURING_FINISH		= 0x01001010,
		//THREADING				= 0x01000001,
		//THREADING_ROUGH			= 0x01000011,
		//THREADING_FINISH		= 0x01000101,
		//KNURLING				= 0x01000011,
		//KNURLING_ROUGH			= 0x01000111,
		//KNURLING_FINISH			= 0x01001011
		//// TURNING MACHINING =================

		UNDEFINED_OPERATION		= 0,

		// MACHINING OPERATION ===============
		MILLING_MACHINING		= 10000,
		TURNING_MACHINING		= 20000,
		// MACHINING OPERATION ===============

		// MILLING MACHINING =================
		MILLING_TYPE			= 11000,
		FREEFORM_OPERATION		= 11100, 
		TWO5D_MILLING_OPERATION	= 11200,

		// DRILLING TYPE
		DRILLING_TYPE			= 12000,

		DRILLING_OPERATION		= 12100, 
		// DRILLING_TYPE -> DRILLING_OPERATION
		DRILLING				= 12101,
		CENTER_DRILLING			= 12102,
		COUNTER_SINKING			= 12103,
		MULTISTEP_DRILLING		= 12104,

		BORING_OPERATION		= 12105, 
		BACK_BORING				= 12106, 
		TAPPING					= 12107, 
		THREAD_DRILLING			= 12108,
		// MILLING MACHINING =================

		// TURNING MACHINING =================
		FACING					= 20001,
		FACING_ROUGH			= 20002,
		FACING_FINISH			= 20003,
		GROOVING				= 20004,
		GROOVING_ROUGH			= 20005,
		GROOVING_FINISH			= 20006,
		CONTOURING				= 20007,
		CONTOURING_ROUGH		= 20008, 
		CONTOURING_FINISH		= 20009,
		THREADING				= 20010,
		THREADING_ROUGH			= 20011,
		THREADING_FINISH		= 20012,
		KNURLING				= 20013,
		KNURLING_ROUGH			= 20014,
		KNURLING_FINISH			= 20015
		// TURNING MACHINING =================
	};
 `
 
 ### TurningMachiningOperation extends machiningOperation
  - Integer tooltipPosition
  - TurningApproachRetractStrategy approach
  - TurningApproachRetractStrategy retract
  - Integer subOperationType
  `
  enum E_SUB_OPERATION_TYPE 
	{ 
		ROUGH=0, 
		FINISH=1
	};
  `
  
  ## FeedSelect
   - Double feedPerRevolution
   - Double feedSpeed
   
  ## MachiningStrategy
   `
   enum MACHINING_STRATEGY
	{
		//UNDEFINED							= 0x000000,

		//// TURNING 
		//TURNING_MACHINING_STRATEGY			= 0x010000,
		//UNIDIRECTIONAL_TURNING				= 0x011000,
		//BIDIRECTIONAL_TURNING				= 0x010100,
		//CONTOUR_TURNING						= 0x010010,
		//THREAD_STRATEGY						= 0x010001,
		//GROOVING_STRATEGY					= 0x010011,
		//UNIDIRECTIONAL_GROOVING				= 0x010111,
		//EXPLICIT_TURNING_STRATEGY			= 0x011111,


		//// MILLING
		//MILLING_MACHINING_STRATEGY			= 0x100000,
		//FEEFORM_STRATEGY					= 0x100100,
		//TWO5D_MILLING_STRATEGY				= 0x110000,

		//// MILLING -> DRILLING
		//DRILLING_TYPE_STRATEGY				= 0x101000,


		UNDEFINED							= 0,

		// TURNING 
		TURNING_MACHINING_STRATEGY			= 10000,
		UNIDIRECTIONAL_TURNING				= 11000,
		BIDIRECTIONAL_TURNING				= 12000,
		CONTOUR_TURNING						= 13000,
		THREAD_STRATEGY						= 14000,
		GROOVING_STRATEGY					= 15000,
		UNIDIRECTIONAL_GROOVING				= 15100,
		BIDIRECTIONAL_GROOVING				= 15200,
		RAMPING_GROOVING					= 15300,
		CONTOUR_GROOVING					= 15400,
		EXPLICIT_TURNING_STRATEGY			= 16000,


		// MILLING
		MILLING_MACHINING_STRATEGY			= 20000,
		// Milling->
		FEEFORM_STRATEGY					= 21000,
		// Milling->
		TWO5D_MILLING_STRATEGY				= 22000,

		// MILLING -> DRILLING
		DRILLING_TYPE_STRATEGY				= 23000
	};
   `
### MillingMachininigStrategy extends MachiningStrategy

### WorkingStep extends Executable
 - ElementarySurface secplane

#### MachiningWorkingStep extends WorkingStep
 - ManufacturingFeature feature
 - MachiningOperation operation
 - InProcessGeometry itsEffect
 
### InProcessGeometry extends ProcessData
 - List<Curve> asIs
 - List<Curve> toBe
 - List<Curve> removal
  
## ManufacturingFeature
 - String id
 - String workpieceId
 - List<String> operationIds
 - Workpiece workpiece
 - List<MachiningOperation> operations
 `
  enum E_MANUFACTURING_FEATURE
	{
		UNDEFINED_FEATURE_TYPE=0x00000000,

		// REGION
		REGION						= 10000,//0x01000000,
		// REGION ->
		REGION_SURFACE_LIST			= 11000,
		REGION_PROJECTION			= 12000,
		TOPOLOGICAL_REGION			= 13000,
		
		// TWO5D_MANUFACTURING_FEATURE
		TWO5D_MANUFACTURING_FEATURE = 20000,//0x10000000,
		// TWO5D -> For Milling, subtype of two5d
		MACHINING_FEATURE			= 21000,//0x11000000,
		// TWO5D -> MACHINING_FEATURE
		PLANAR_FACE					= 21010,//0x11100000,
		POCKET						= 21020, //0x11010000,
		SLOT						= 21030,//0x11001000,
		STEP						= 21040,//0x11000100,
		ROUND_HOLE					= 21050,//0x11000010,
		TOOLPATH_FEATURE			= 21060,//0x11000001,
		PROFILE_FEATURE				= 21070,//0x11000011,
		BOSS						= 21080,//0x11000101,
		SPHERICAL_CAP				= 21090,//0x11001001,
		ROUNDED_END					= 21100,//0x11010001,
		THREAD						= 21110,//0x11100001,
		// TWO5D -> MACHINING_FEATURE -> THREAD
		CATALOGUE_THREAD			= 21111,//0x11100011,
		DEFINED_THREAD				= 21112,//0x11100101,
		// TWO5D ->
		REPLICATE_FEATURE			= 22000,//0x11,
		// TWO5D -> REPLICATE_FEATURE
		RECTANGULAR_PATTERN			= 22010,
		CIRCULAR_PATTERN			= 22020,
		GENERAL_PATTERN				= 22030,
		// TWO5D -> 
		COMPOUND_FEATURE			= 23000,

		// TRANSITION_FEATURE 	
		TRANSITION_FEATURE			= 30000,//0x00100000,
		// TRANSITION_FEATURE ->
		CHAMFER						= 31000,
		EDGE_ROUND					= 32000,

		// For turning, subtype of two5d
		// TWO5D ->
		TURNING_FEATURE				= 24000, //0x10100000,

		OUTER_ROUND					= 24010, //0x10110000,
		
		REVOLVED_FEATURE			= 24020, //0x10101000,
		REVOLVED_ROUND				= 24021, //0x10101100,
		REVOLVED_FLAT				= 24022, //0x10101010,
		GROOVE						= 24023, //0x10101001,
		GENERAL_REVOLUTION			= 24024, //0x10101011
		
		KNURL						= 24030, //0x10100100,
		STAIGHT_KNURL				= 24031,
		DIAGONAL_KNURL				= 24032,
		DIAMOND_KNURL				= 24033,
		TOOL_KNURL					= 24034
	};
	`
### Two5dManufacturingFeature extends ManufacturingFeature
 - Axis2Placement3d featurePlacement
 
#### MachiningFeature extends Two5dManufacturingFeature
 - TolerancedLengthMeasure depth
 - TolerancedLengthMeasure planarRadius
 - TolerancedLengthMeasure orthogonalRadius
 
##### RoundHole extends MachiningFeature
 - TolerancedLengthMeasure diameter
 - TaperSelect changeInDiameter
 - BottomCondition bottomCondition
 
### Region extends ManufacturingFeature
 - Axis2Placement3d featurePlacement
 
### TransitionFeature extends ManufacturingFeature
 - MachiningFeature firstFeature
 - MachiningFeature secondFeature
 
#### TurningFeature extends Two5dManufacturingFeature
 - List<Curve> curvesOfFeature
 
### MillingMachiningOperation extends MachiningOperation
 - ApproachRetractStrategy approach
 - ApproachRetractStrategy retract
 
#### MillingTypeOperation extends MillingMachiningOperation

### RapidMovement extends WorkingStep, Operation

#### RapidMovementReturnHome extends RapidMovement
 - Point viaPoint

#### RapidMovementSecPlane extends RapidMovement
 - Vector direction
 - Surface secPlane
