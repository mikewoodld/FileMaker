<b>Calculation Fields used in Session 2.2</b>


Gobos in use

        If (IsEmpty (Count (Instruments::Gobo));0;Count (Instruments::Gobo))

Gobos Remaining

        Abs ( qtyStock-qtyInUse )

Instrument Types In Use (qty)

        If (IsEmpty (Count (Instruments::Instrument Type));0;Count (Instruments::Instrument Type))

Types Remain

        qtyStock-qtyInUse

Units on Position

        If (IsEmpty (Count (Instruments::Position));0;Count (Instruments::Position))

Position Total Weight

        (Sum ( Instruments::Weight ))+weightTare
