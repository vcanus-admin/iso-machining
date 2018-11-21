# EndPosition
 - x, y, z, u, v, w, a, b, c
 
# NCBlock
 - Integer type
 - MachiningProject
 - Workplan
 - Executable
 - MachiningOperation
 - List<ToolPath>
 - ToolPath
 - Integer blockNumber
 - Curve curve
 - Curve curveForAirCut
 - Integer currentFeed
 - Integer currentSpindle
 - EndPosition startPosition
 - EndPosition endPosition
 - NCBlock prevBlock
 - NCBlock nextBlock
 - String ncCode
 - BehaviorNCBlock behaviorNCBlock
 
 `
 enum E_NCBLOCK_TYPE
	{
		UNDEFINED				= 0,
		MOTION					= 10000,
		STATE					= 20000,

		MOTION_LINEAR			= 10100,
		MOTION_CIRCULAR			= 10200,
		MOTION_NURBS			= 10300,
		MOTION_THREAD			= 0x100010,
		MOTION_DWELL			= 10400,

		MOTION_LINEAR_CUTTING	= 10110,
		MOTION_LINEAR_RAPID		= 10120,

		MOTION_CIRCULAR_CCW		= 10210,
		MOTION_CIRCULAR_CW		= 10220,

		TOOLCHANGE				= 20001,
		T_CODE					= 20002
	};
  `
 
## Approach extends NCBlock

## Retract extends NCBlock

## ToolChange extends NCBlock

## TCode extends NCBlock

## OptionalStop extends NCBlock

## MotionBlock extends NCBlock

### LinearMotionBlock extends MotionBlock
 - x, y, z, u, v, w, a, b, c

#### LinearRapidMotionBlock extends LinearMotionBlock

### CircularMotionBlock extends MotionBlock
 - x, y, z, i, j, k, R
 
#### CCWCircularMotionBlock extends CircularMotionBlock

#### CWCircularMotionBlock extends CircularMotionBlock

### NURBSMotionBlock extends MotionBlock

### DwellMotionBlock extends MotionBlock

## StateBlock extends NCBlock
