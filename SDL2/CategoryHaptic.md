# CategoryHaptic

SDL haptic subsystem allows you to control haptic (force feedback) devices.

The basic usage is as follows:

- Initialize the subsystem ([SDL_INIT_HAPTIC](SDL_INIT_HAPTIC)).
- Open a haptic device.
- [SDL_HapticOpen](SDL_HapticOpen)() to open from index.
- [SDL_HapticOpenFromJoystick](SDL_HapticOpenFromJoystick)() to open from
  an existing joystick.
- Create an effect ([SDL_HapticEffect](SDL_HapticEffect)).
- Upload the effect with [SDL_HapticNewEffect](SDL_HapticNewEffect)().
- Run the effect with [SDL_HapticRunEffect](SDL_HapticRunEffect)().
- (optional) Free the effect with
  [SDL_HapticDestroyEffect](SDL_HapticDestroyEffect)().
- Close the haptic device with [SDL_HapticClose](SDL_HapticClose)().

Simple rumble example:

```c
   SDL_Haptic *haptic;

   // Open the device
   haptic = SDL_HapticOpen( 0 );
   if (haptic == NULL)
      return -1;

   // Initialize simple rumble
   if (SDL_HapticRumbleInit( haptic ) != 0)
      return -1;

   // Play effect at 50% strength for 2 seconds
   if (SDL_HapticRumblePlay( haptic, 0.5, 2000 ) != 0)
      return -1;
   SDL_Delay( 2000 );

   // Clean up
   SDL_HapticClose( haptic );
```

Complete example:

```c
int test_haptic( SDL_Joystick * joystick ) {
   SDL_Haptic *haptic;
   SDL_HapticEffect effect;
   int effect_id;

   // Open the device
   haptic = SDL_HapticOpenFromJoystick( joystick );
   if (haptic == NULL) return -1; // Most likely joystick isn't haptic

   // See if it can do sine waves
   if ((SDL_HapticQuery(haptic) & SDL_HAPTIC_SINE)==0) {
      SDL_HapticClose(haptic); // No sine effect
      return -1;
   }

   // Create the effect
   SDL_memset( &effect, 0, sizeof(SDL_HapticEffect) ); // 0 is safe default
   effect.type = SDL_HAPTIC_SINE;
   effect.periodic.direction.type = SDL_HAPTIC_POLAR; // Polar coordinates
   effect.periodic.direction.dir[0] = 18000; // Force comes from south
   effect.periodic.period = 1000; // 1000 ms
   effect.periodic.magnitude = 20000; // 20000/32767 strength
   effect.periodic.length = 5000; // 5 seconds long
   effect.periodic.attack_length = 1000; // Takes 1 second to get max strength
   effect.periodic.fade_length = 1000; // Takes 1 second to fade away

   // Upload the effect
   effect_id = SDL_HapticNewEffect( haptic, &effect );

   // Test the effect
   SDL_HapticRunEffect( haptic, effect_id, 1 );
   SDL_Delay( 5000); // Wait for the effect to finish

   // We destroy the effect, although closing the device also does this
   SDL_HapticDestroyEffect( haptic, effect_id );

   // Close the device
   SDL_HapticClose(haptic);

   return 0; // Success
}
```

<!-- END CATEGORY DOCUMENTATION -->

## Functions

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryHaptic, CategoryAPIFunction -->
- [SDL_HapticClose](SDL_HapticClose)
- [SDL_HapticDestroyEffect](SDL_HapticDestroyEffect)
- [SDL_HapticEffectSupported](SDL_HapticEffectSupported)
- [SDL_HapticGetEffectStatus](SDL_HapticGetEffectStatus)
- [SDL_HapticIndex](SDL_HapticIndex)
- [SDL_HapticName](SDL_HapticName)
- [SDL_HapticNewEffect](SDL_HapticNewEffect)
- [SDL_HapticNumAxes](SDL_HapticNumAxes)
- [SDL_HapticNumEffects](SDL_HapticNumEffects)
- [SDL_HapticNumEffectsPlaying](SDL_HapticNumEffectsPlaying)
- [SDL_HapticOpen](SDL_HapticOpen)
- [SDL_HapticOpened](SDL_HapticOpened)
- [SDL_HapticOpenFromJoystick](SDL_HapticOpenFromJoystick)
- [SDL_HapticOpenFromMouse](SDL_HapticOpenFromMouse)
- [SDL_HapticPause](SDL_HapticPause)
- [SDL_HapticQuery](SDL_HapticQuery)
- [SDL_HapticRumbleInit](SDL_HapticRumbleInit)
- [SDL_HapticRumblePlay](SDL_HapticRumblePlay)
- [SDL_HapticRumbleStop](SDL_HapticRumbleStop)
- [SDL_HapticRumbleSupported](SDL_HapticRumbleSupported)
- [SDL_HapticRunEffect](SDL_HapticRunEffect)
- [SDL_HapticSetAutocenter](SDL_HapticSetAutocenter)
- [SDL_HapticSetGain](SDL_HapticSetGain)
- [SDL_HapticStopAll](SDL_HapticStopAll)
- [SDL_HapticStopEffect](SDL_HapticStopEffect)
- [SDL_HapticUnpause](SDL_HapticUnpause)
- [SDL_HapticUpdateEffect](SDL_HapticUpdateEffect)
- [SDL_JoystickIsHaptic](SDL_JoystickIsHaptic)
- [SDL_MouseIsHaptic](SDL_MouseIsHaptic)
- [SDL_NumHaptics](SDL_NumHaptics)
<!-- END CATEGORY LIST -->

## Datatypes

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryHaptic, CategoryAPIDatatype -->
- (none.)
<!-- END CATEGORY LIST -->

## Structs

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryHaptic, CategoryAPIStruct -->
- [SDL_HapticCondition](SDL_HapticCondition)
- [SDL_HapticConstant](SDL_HapticConstant)
- [SDL_HapticCustom](SDL_HapticCustom)
- [SDL_HapticDirection](SDL_HapticDirection)
- [SDL_HapticEffect](SDL_HapticEffect)
- [SDL_HapticLeftRight](SDL_HapticLeftRight)
- [SDL_HapticPeriodic](SDL_HapticPeriodic)
- [SDL_HapticRamp](SDL_HapticRamp)
<!-- END CATEGORY LIST -->

## Enums

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryHaptic, CategoryAPIEnum -->
- (none.)
<!-- END CATEGORY LIST -->

## Macros

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryHaptic, CategoryAPIMacro -->
- [SDL_HAPTIC_AUTOCENTER](SDL_HAPTIC_AUTOCENTER)
- [SDL_HAPTIC_CARTESIAN](SDL_HAPTIC_CARTESIAN)
- [SDL_HAPTIC_CONSTANT](SDL_HAPTIC_CONSTANT)
- [SDL_HAPTIC_CUSTOM](SDL_HAPTIC_CUSTOM)
- [SDL_HAPTIC_DAMPER](SDL_HAPTIC_DAMPER)
- [SDL_HAPTIC_FRICTION](SDL_HAPTIC_FRICTION)
- [SDL_HAPTIC_GAIN](SDL_HAPTIC_GAIN)
- [SDL_HAPTIC_INERTIA](SDL_HAPTIC_INERTIA)
- [SDL_HAPTIC_INFINITY](SDL_HAPTIC_INFINITY)
- [SDL_HAPTIC_LEFTRIGHT](SDL_HAPTIC_LEFTRIGHT)
- [SDL_HAPTIC_PAUSE](SDL_HAPTIC_PAUSE)
- [SDL_HAPTIC_POLAR](SDL_HAPTIC_POLAR)
- [SDL_HAPTIC_RAMP](SDL_HAPTIC_RAMP)
- [SDL_HAPTIC_SAWTOOTHDOWN](SDL_HAPTIC_SAWTOOTHDOWN)
- [SDL_HAPTIC_SAWTOOTHUP](SDL_HAPTIC_SAWTOOTHUP)
- [SDL_HAPTIC_SINE](SDL_HAPTIC_SINE)
- [SDL_HAPTIC_SPHERICAL](SDL_HAPTIC_SPHERICAL)
- [SDL_HAPTIC_SPRING](SDL_HAPTIC_SPRING)
- [SDL_HAPTIC_STATUS](SDL_HAPTIC_STATUS)
- [SDL_HAPTIC_STEERING_AXIS](SDL_HAPTIC_STEERING_AXIS)
- [SDL_HAPTIC_TRIANGLE](SDL_HAPTIC_TRIANGLE)
<!-- END CATEGORY LIST -->

