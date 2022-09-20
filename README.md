# MagmaPolred

This provides the following intrinsics
- `intrinsic Polred(f::RngUPolElt : Best:="dynamic") -> RngUPolElt, SeqEnum, BoolElt`
- `intrinsic Polredabs(f::RngUPolElt) -> RngUPolElt, SeqEnum, BoolElt`
- `intrinsic Polredbest(f::RngUPolElt) -> RngUPolElt, SeqEnum, BoolElt`
- `intrinsic Polredbestabs(f::RngUPolElt) -> RngUPolElt, SeqEnum, BoolElt`
- `intrinsic Polred(K::Fld : Best:="dynamic") -> FldNum, Map, BoolElt`
- `intrinsic Polredbest(K::Fld) -> FldNum, Map, BoolElt`
- `intrinsic Polredbest(K::Fld) -> FldNum, Map, BoolElt`
- `intrinsic Polredbestabs(K::Fld) -> RngUPolElt, Map, BoolElt`


## Prerequisites

For optimal results, set your Pari stack size to a decent size by for example adding
```
parisize = "4096M"
```
to your `~/.gprc` file. This is an optional improvement.

## Documentation
See the official `gp/pari` documentation webpage:
http://pari.math.u-bordeaux.fr/dochtml/html-stable/General_number_fields.html#polredabs

## Examples

```
> AttachSpec("spec");
> f := t^2 - 5;
> Polredabs(f);
t^2 - t - 1
[ 1, -2 ]
true
> L<a> := NumberField(f);
> Polredabs(L);
Number Field with defining polynomial t^2 - t - 1 over the Rational Field
Mapping from: FldNum: L to Number Field with defining polynomial t^2 - t - 1 over the Rational Field
true
> g := t^12 + 8*t^8 - 50*t^6 + 16*t^4 - 3069*t^2 + 625;
> time Polredbest(g);
t^12 + 12*t^10 - 8*t^8 - 3135*t^6 + 472*t^4 + 44*t^2 + 1
[ 0, 36515747/5969767, 0, 2215118934/5969767, 0, -10667302939/5969767, 0, -29547723/5969767, 0, 40643881/5969767, 0, 3403173/5969767 ]
true
Time: 0.020
> time Polredabs(g);
t^12 + 8*t^8 - 50*t^6 + 16*t^4 - 3069*t^2 + 625
[ 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ]
true
Time: 0.030
> time Polredbestabs(g);
t^12 + 8*t^8 - 50*t^6 + 16*t^4 - 3069*t^2 + 625
[ 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ]
true
Time: 0.050[r]
```
