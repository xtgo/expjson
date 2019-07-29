This is a fork of the 1.12 stdlib encoding/json.

This fork differs in the following ways:

- Encoder.SetNonNull(true) outputs brackets/braces for empty slices and maps.
- In handling omitempty, Marshal (and Encode) first call a value's IsZero
  method if present, omitting the element if IsZero returns true, while
  including the value if false.
- In handling omitempty, structs that don't have an IsZero method will be
  omitted if they have the zero value.
- Map keys that are both string-kinded as well as an encoding.TextMarshaler
  will use the MarshalText method when encoding.
- Map keys that are both string-kinded as well as an encoding.TextUnmarshaler
  will use the UnmarshalText method when decoding.
