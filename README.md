# monarch-behavior-management
Sample of Behavior Management module of MOnarCH project

This code implements a ROS node called Local Behavior Manager (LBM). It is
part of the code base for the MOnarCH project and, in particular, it
belongs to the behavior management module (containing several other 
components). It is executed in each robot of the team and controls the
start and finish (including preemption) of multiple concorrent 
behaviors. It receives as inputs behavior execution/cancelation requests
from a centralized node that communicates with a global planner. The 
interface to do so are SAM slots. These are akin to shared topics that
are synchronized in multiple ROS masters. Each behavior is represented
in the LBM as an actionlib client (with the behavior being implemented
in the respective actionlib server). An abstract actionlib client message
is used to generalize communication between the LBM and all the actionlib
clients. It manages resources (actuators) used by each behavior, forbiding
concurrent execution of behaviors which use the same resource. It also
keeps other ROS masters in the system (such as the global planner) aware
of the state of execution and result (upon termination) of each behavior
as well as what behaviors the robot is currently executing.

Development of this node occured during the middle of the MOnarCH project
lifetime (2014-2015).
