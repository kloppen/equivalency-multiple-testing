# Purpose of this Repository
This repo is intended for code, ideas and discussion related to applying
multiple testing corrections, and similar techniques to equivalency
programs for Additive Manufacturing.

For some AM materials and PMC materials, a large test program is performed
to characterize the material. This test program is referred to as the
qualification test program. A- and B-Basis values (lower tolerance
limits) are determined from the qualification data for the properties
included in the test program. These A- and B-Basis values are used to set
Design Values which are relied upon when designing parts made from the material.

Equivalency testing is typically used in two scenarios:

1. *Lot Acceptance:* When a new lot/batch of material is procured from the
  material manufacturer, a smaller data set with a few material properties
  is obtained. This "acceptance" sample is compared with the qualification
  sample to determine if the new lot of material is similar enough to the
  material used for the material qualification. This ensures that the Design
  Values developed for the material are valid for the new lot of material,
  and hence parts made with the new lot of material will be of the expected
  strength.

2. *Process/Site/Machine Equivalency:* When a change is made to the
  manufacturing process, or a new manufacturing site is introduced
  (for example, parts will be made by a sub-tier) or in the case of AM
  material, a new machine is introduced, testing must be conduced to ensure
  that the material processed using the new process/site/machine is similar
  enough to material processed for the qualification program. This ensures
  that parts made using the new process/site/machine will have the expected
  strength and the Design Values remain valid.

For AM materials, many different material properties are included in
a process/site/machine equivalency test program. This means that many
hypothesis tests are performed and hence the chance of at least one Type I
error being made is quite high.

Historically, engineers have used "engineering judgement" to accept
equivalency samples that are rejected by the hypothesis test. This is not
necessarily done in a rigorous way: it is sometimes based on rejecting
the null hypothesis "only by a little bit" or by considering how important
the material property for the rejected test is to the part design.

A more rigorous approach is sought.


# Ideas that could be explored
- Controlling FWER using the Holm's test
- Controlling FDR using the Benjamini-Hochberg procedure
- Consider correlation between material properties:
  - For example, if we tested a material at three different temperatures (cold,
    room-temperature and hot) and
    three different mechanical tests (tension, compression, shear).
    Assume that there ought to be correlation between material properties
    and temperatures. If we rejected the hypothesis test for all of the
    hot tests (hot/tension, hot/compression and hot/shear were all rejected),
    there is a lot of evidence that there is a problem with the
    material/process. There would be less evidence that there is a problem
    with the material/process if we rejected cold/tension, room-temp/compression
    and hot/shear (assuming that these property/temperatures are expected
    to have less correlation).
