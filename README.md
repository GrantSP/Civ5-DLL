Civ5-DLL
========

[CvTacticalAI]
==============

New:
----

void GetBestPlot (Get the best plot on a vector based on danger)

bool ContainsPlot (not used - check best plot based on range looking on a plot vector list)

int SamePlotFound (Get the number of occurrences of a same plot in a plot vector list)

CvPlot* GetBestRepositionPlot (get the best reposition plot for a unit witch want to range attack out of range)

bool FindAirUnitsToAirSweep (get possible air sweeps by air units on target)

Modified:
---------

bool CvTacticalAI::PlotCaptureCityMoves() (Now doesn't use ranged with city at 1HP).

bool CvTacticalAI::PlotDamageCityMoves() (Now doesn't use ranged with city at 1HP).

void CvTacticalAI::PlotAirInterceptMoves() (Reworked to do not overuse intercept moves).

void CvTacticalAI::ExecuteAttack (rearranged and added ranged move prior to fire)

bool CvTacticalAI::FindUnitsWithinStrikingDistance (add distance + movement on ranged)

int CvTacticalAI::ComputeTotalExpectedDamage (distance + movement counts half damage)

void CvTacticalAI::ExecuteMovesToSafestPlot() (now try to avoid water tiles if there's no cover and will embark to do so)

[CvUnit]
========

New:
----

int CvUnit::GetRangePlusMoveToshot (property to tell a distance witch may move and shoot)

void CvUnit::GetMovablePlotListOpt (select movable plots with movement left in a range of plots towards target)

bool CvUnit::canEverRangeStrikeAtFromPlot (overload of function with plot as parameter)

bool CvUnit::canMoveAndRangedStrike (not used - tells if unit could move and then range shot to target)

CvUnit::GetPromotionValue (Helper to calculate promotion values on a centralized function)

Modified:
---------

int CvUnit::AI_promotionValue (Reworked entirely to make promotions more random and higher priority on better ones)

bool CvUnit::canEverRangeStrikeAt (original function now is an overload)

[CvDangerPlots]
===============

Modified:
---------

void CvDangerPlots::AssignUnitDangerValue (now takes ranged units into acount properly)

[CvMilitaryAI]
==============

New:
----

int GetMaxPossibleInterceptions (Get all possible interceptions on that plot)

Modified:
---------

int CvMilitaryAI::GetNumEnemyAirUnitsInRange (add half range of the current unit looking for other air units as the desired distance).

bool MilitaryAIHelpers::IsTestStrategy_NeedAirCarriers (also check for not having more carrier than the 20% of the total naval units)

[CvHomelandAI]
==============

Modified:
---------

void CvHomelandAI::EstablishHomelandPriorities() (up priority for upgrade on even turns so AI is able to upgrade air units).

void CvHomelandAI::PlotFirstTurnSettlerMoves() (bug fix not checking unit)

void CvHomelandAI::PlotHealMoves() (heal only if less than 75% hit points on a danger zone)

void CvHomelandAI::PlotMovesToSafety() (now takes into account the current combat modifier for fleeing for very unfavorable condition)

void CvHomelandAI::ExecuteMovesToSafestPlot() (now try to avoid water tiles if there's no cover and will embark to do so)

void CvHomelandAI::PlotAircraftMoves() (Added interception moves prior to moving units).

void CvHomelandAI::ExecuteArchaeologistMoves() (Modified to scrap archaeologists under certain conditions)

void CvHomelandAI::PlotUpgradeMoves() (Also upgrade if unit is in army but is not active, bonus upgrade if many units to upgrade)

New:
----

void CvHomelandAI::ExecuteAircraftInterceptions() (Similar to interception moves on tactical AI, grant some interceptions based on number of enemies).

[CvPlayerAI]
============

Modified:
---------

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveWriter (Wait some turns if not able to make work and want to)

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveArtist (Wait for some turns, Brazil wait a bit more to start spending them)

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveMusician (Wait some turns if not able to make work and want to)

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveMerchant (If very early, AI will build those customs house)

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveScientist (AI will build academies much more often)

GreatPeopleDirectiveTypes CvPlayerAI::GetDirectiveProphet(CvUnit*) (Sometimes build holy sites if got prophet very early)


[CvDealAI]
==========

Modified:
---------

void CvDealAI::DoAddVoteCommitmentToThem (Doesn't add a vote resolution if it's of no value)

void CvDealAI::DoAddVoteCommitmentToUs (Doesn't add a vote resolution if it's of no value)

void CvDealAI::DoAddResourceToThem (Doesn't add a resource if it's of no value)

void CvDealAI::DoAddResourceToUs (Doesn't add a resource if it's of no value)

void CvDealAI::DoAddEmbassyToThem (Doesn't add an embassy if it's of no value)

void CvDealAI::DoAddEmbassyToUs (Doesn't add an embassy if it's of no value)

void CvDealAI::DoAddOpenBordersToThem (Doesn't add open borders if it's of no value)

void CvDealAI::DoAddOpenBordersToUs (Doesn't add open borders if it's of no value)

[CvCityStrategyAI]
==================

Modified:
---------

bool CityStrategyAIHelpers::IsTestCityStrategy_NeedTileImprovers (Upped conditions to make more workers under certain conditions)

[CvPlayer]
==========

New:
----

int CvPlayer::countCitiesCoastalLessValue() (helper function to check out cities for need tile improvements).

[CvCity]
========

New:
----

bool CvCity::IsCanGoldPurchase (check for gold purchase based on a city order)

void CvCity::PurchaseCurrentOrder() (Purchase what is being built on a city).

[CvEconomicAI]
==============

Modified:
---------

void CvEconomicAI::DoTurn() (Added call to DisbandLongObsoleteUnits)

void CvEconomicAI::DoHurry() (Reworked and re-activated: Check to rush units and buildings under certain conditions)

void CvEconomicAI::DisbandExtraWorkers() (Look for disband at 3 gpt per unit too to disband a bit more aggressively)

bool EconomicAIHelpers::IsTestStrategy_EnoughArchaeologists (change archaeologist to sites ratio to half value)

New:
----

void CvEconomicAI::DisbandLongObsoleteUnits() (Disband long obsolete units like ancient units at industrial era)

[CvGrandStrategyAI]
===================

Modified:
---------

int CvGrandStrategyAI::GetCulturePriority() (Lowered a little values per era)

int CvGrandStrategyAI::GetSpaceshipPriority() (Upped a lot the values per era)


[CvPolicyAI]
============

Modified:
---------
CvPolicyAI::ChooseNextPolicy (No pre-requirement/ancient policies are rated a bit less)

[CvPolicyClasses]
=================

Modified:
---------

void CvPlayerPolicies::AddFlavorAsStrategies (Don't factor in Grand strategy before Medieval)

New:
----

bool CvPlayerPolicies::IsEraPrereqBranch (Check if a policy has pre-requirements)