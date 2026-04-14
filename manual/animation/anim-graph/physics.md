# Physics

Anim Graph can run a simple physical simulation on certain bones to enrich the visuals of the characters or animated objects. Physics can be partially controlled by animation, for example, the root node of the Spring Bone chain driven by animation, to provide a realistic link between artist-authored animation and runtime-generated animation.

> [!Tip]
> Physical simulation runs in world-space, meaning the animated skeleton pose is automatically converted from local node-space and back.

## Spring Bone Physics

| OFF | ON |
|--------|--------|
| ![Without Spring Bone Physics](media/spring-bone-off.gif) | ![With Spring Bone Physics](media/spring-bone-on.gif) |

**Spring Bone Physics** node simulates soft, physics-based trailing motion―like antennae, tails, or cloth strips―for a connected chain of skeletal bones. Set `End Ndoe` and `Nodes` count to define a chain of bones in your character or object. The root bone stays fixed to your normal animation, while each subsequent bone follows along with dynamic, secondary motion (sway, flutter, jiggle), automatically reacting to gravity, wind, and movement in a natural way. You can control how stiff, heavy, or flexible the bones feel, limit how sharply they can move, and combine with any standard animation system (this preserves your character's main animations, only affecting the simulated bones).

Typical use cases: animated tails, wiggle hair, bunny ears, rope, tentacles, trailing wires, and antennas.

![Spring Bone Physics Node](media/spring-bone-node.png)

| Property | Description |
|--------|--------|
| **End Node** | The last (tip) node of the spring bones chain to simulate. |
| **Nodes** | Amount of nodes in a chain to simulate, starting from the End Node going up in the hierarchy. Excluding root node the chain is attached to. |
| **Weight** | Alpha parameter that can blend between animated pose and simulated pose. `0` - fully animated, `1` - fully simulated. |
| **Stiffness** | Defines how stiff the joints between bones are. `0` - limp, `1` = rigid. |
| **Drag** | The scale of velocity applied to bones. The greater the value, the more suppressed the movement. Lower values increase movement freedom. |
| **Stretch Limit** | The maximum bones stretch scale. `0` - no stretch, `1` - can stretch up to double length. |
| **Gravity Scale** | The world gravity scale. Can be used to adjust gravity force or disable it. |
| **Force** | The additional, external force applied to rope (world-space). This can be eg. wind force. |
