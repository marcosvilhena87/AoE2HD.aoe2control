# Catálogo de assinaturas Lua públicas — extração auditável

Data: 2026-10-20. Fontes: [declarações](https://github.com/aoe2control/aoe2-control-lua-vscode-extension/blob/main/definitions/control-api.d.lua), [documentação](https://github.com/aoe2control/aoe2control.github.io/tree/main/docs). Declaração Lua é uma referência estática da extensão: **não comprova** implementação no motor distribuído nem presença na versão HD.

**Escopo:** funções e métodos declarados. Não inclui edição de mapas aleatórios (RMSIDE). Métodos de consulta de terreno, caminhos e permissões de construção são mantidos por interessarem ao controle de unidades.

Total de ocorrências declaradas: **380**; assinaturas distintas: **380**. A coluna Docs aponta páginas onde a grafia completa do símbolo aparece literalmente (checagem aproximada por texto, não validação semântica). Ausência na coluna não significa API inexistente.

## Global (136)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Load(assignedPlayerId)` | `commands`, `facts`, `enums`, `lifecycle`, `module-system`, `settings-api`, `limits`, `session-control`, `game-options` |
| `Init()` | `facts`, `types`, `lifecycle`, `ipc-api`, `limits`, `session-control` |
| `Update()` | `commands`, `facts`, `types`, `enums`, `lifecycle`, `interface-options`, `ipc-api`, `settings-api`, `render-api`, `limits` |
| `Render()` | `commands`, `facts`, `types`, `enums`, `lifecycle`, `interface-options`, `settings-api`, `render-api`, `limits`, `headless-mode` |
| `End(hasWon)` | `facts`, `enums`, `lifecycle`, `limits`, `session-control` |
| `Unload()` | `lifecycle`, `interface-options` |
| `Vector2(x, y)` | `commands`, `facts`, `types`, `settings-api`, `render-api` |
| `Vector3(x, y, z)` | `commands`, `facts`, `types`, `render-api` |
| `Vector4(x, y, z, w)` | `types` |
| `Log(message)` | `commands`, `facts`, `types`, `enums`, `module-system`, `interface-options`, `ipc-api`, `limits`, `session-control`, `game-options` |
| `SetEngineUIVisibility(visible)` | `commands`, `limits`, `session-control` |
| `UnloadEngine()` | `commands`, `limits`, `session-control` |
| `SetGameSpeedMultiplier(multiplier)` | `commands`, `interface-options`, `agent-bridge`, `limits` |
| `IsMenuOpen()` | `commands`, `limits` |
| `DispatchStartGame()` | `commands`, `agent-bridge`, `limits`, `session-control`, `game-options` |
| `DispatchRestartGame()` | `commands`, `limits`, `session-control` |
| `DispatchResignGame()` | `commands`, `limits`, `session-control` |
| `DispatchQuitGame()` | `commands`, `limits`, `session-control` |
| `DispatchLoadGame(saveGameFileName)` | `commands`, `limits`, `session-control` |
| `GetAvailableSaveFiles()` | `commands`, `limits`, `session-control` |
| `GetCurrentGameOptions()` | `commands`, `types`, `session-control`, `game-options` |
| `SetCameraPosition(position)` | `commands`, `limits` |
| `SendChatMessage(message)` | `commands`, `limits` |
| `TrainUnit(trainSources, unitId, amount)` | `commands`, `types`, `enums` |
| `UnitsTargetObject(units, target, queue)` | `commands`, `types` |
| `UnitsBuildStructure(builders, structureId, position)` | `commands` |
| `UnitsMove(units, position, queue)` | `commands` |
| `EnableScouting()` | `commands`, `types` |
| `ResearchTechnology(technology)` | `commands` |
| `DeleteUnit(unit)` | `commands` |
| `DestroyBuilding(building)` | `commands` |
| `SetGatherPoint(buildings, targetPosition)` | `commands` |
| `RingTownBell(building, isCallingIn)` | `commands` |
| `SendBackToWork(building)` | `commands` |
| `SendAllBackToWork(building)` | `commands` |
| `SetUnitStanceAutoScout(units)` | `commands` |
| `SetUnitStancePatrol(units, targetPosition)` | `commands` |
| `SetUnitStanceGuard(units, targetObject)` | `commands` |
| `SetUnitStanceFollow(units, targetObject)` | `commands` |
| `SetUnitStanceAttackMove(units, targetPosition)` | `commands` |
| `SetUnitStanceGarrison(units, targetObject)` | `commands` |
| `SetUnitStanceUngarrison(sourceObjects, unit)` | `commands` |
| `SetUnitStanceSeekShelter(units)` | `commands` |
| `SetUnitCombatStance(units, stance)` | `commands`, `enums` |
| `SetFormation(units, formation)` | `commands`, `enums` |
| `QueueFarmReseeds(amount)` | `commands` |
| `CancelFarmReseeds(amount)` | `commands` |
| `SetAutoFarmReseed(enabled)` | `commands` |
| `QueueFishTrapRebuilds(amount)` | `commands` |
| `CancelFishTrapRebuilds(amount)` | `commands` |
| `SetAutoFishTrapRebuild(enabled)` | `commands` |
| `SetGoal(goalId, value)` | `commands` |
| `SetGoals(firstGoalId, values)` | `commands` |
| `GetFact(factId, parameter)` | `facts`, `types`, `enums`, `limits` |
| `GetUnitTypeCount(unitId)` | `facts`, `types` |
| `GetAttribute(attribute)` | `facts`, `types`, `enums`, `limits` |
| `CanAfford(unitId, isBuilding)` | `facts`, `types` |
| `GetTechCost(technology)` | `facts`, `types`, `enums` |
| `GetObjectCost(unitObjectType, costMultiplier)` | `facts`, `types`, `enums` |
| `IsObjectTypeAvailable(unitObjectType)` | `facts`, `types` |
| `CanResearch(technology)` | `facts`, `types` |
| `IsTechnologyResearched(technology)` | `facts`, `types` |
| `GetObjectsByType(unitType)` | `facts`, `types` |
| `GetObjectsByTypes(unitTypes)` | `facts`, `types` |
| `GetObjectsByClass(unitClass)` | `facts`, `types`, `enums` |
| `GetObjectsByClasses(classes)` | `facts`, `enums` |
| `GetGameTime()` | `facts`, `ipc-api` |
| `GetClockMs()` | `facts`, `limits` |
| `GetModuleTelemetry()` | `facts`, `lifecycle`, `interface-options`, `limits` |
| `GetAllChatMessages()` | `facts` |
| `GetLastChatMessage()` | `facts` |
| `GetNewChatMessages()` | `facts` |
| `IsGamePaused()` | `commands`, `limits` |
| `SetGamePaused(paused)` | `commands`, `limits` |
| `SetReplaySpeed(speed)` | `commands`, `enums`, `limits` |
| `GetCurrentReplayFileName()` | `commands`, `limits` |
| `CalculatePath(from, to, collisionRadius)` | `facts`, `types`, `limits` |
| `GetAssignedPlayer()` | `commands`, `facts`, `types`, `render-api` |
| `GetAssignedPlayerId()` | `commands`, `facts`, `enums`, `lifecycle`, `ipc-api`, `game-options` |
| `AssignAndLoadModule(playerId, moduleName)` | `commands`, `limits` |
| `GetPlayerById(id)` | `facts`, `types`, `enums` |
| `GetPlayerCount()` | `facts` |
| `GetMapTilesPtr()` | `facts`, `ipc-api` |
| `GetMapWidth()` | `facts` |
| `GetMapHeight()` | `facts` |
| `GetMapTile(x, y)` | `facts`, `types`, `limits` |
| `GetAllMapTiles()` | `facts`, `types` |
| `CheckPlacement(objectTypeId, position)` | `commands`, `facts`, `types`, `enums`, `limits` |
| `CanPlaceObject(objectTypeId, position)` | `facts`, `limits` |
| `GetObjectsPtr()` | `facts`, `ipc-api` |
| `GetObjectsInArea(pos1, pos2, unitClass, owner)` | `facts`, `types`, `limits` |
| `GetObjectStates(objects)` | `facts` |
| `GetObjectChanges()` | `facts` |
| `GetObjectTypeData(objectTypeId, objectData)` | `facts`, `enums`, `limits` |
| `GetObjectTypeAttribute(objectTypeId, attribute, damageType)` | `facts`, `enums`, `limits` |
| `IsEnemyPlayer(player)` | `facts` |
| `GetObjectById(id)` | `facts`, `types` |
| `GetProjectileById(id)` | `facts` |
| `GetAllProjectiles()` | `facts` |
| `GetProjectilesByType(projectileType)` | `facts`, `enums` |
| `GetVictoryCondition()` | `facts`, `enums`, `game-options` |
| `GetVictoryPlayer()` | `facts`, `types` |
| `GetScreenSize()` | `render-api`, `limits` |
| `IsOnScreen(position)` | `render-api`, `limits` |
| `RenderText(text, position, size, color, center, border)` | `commands`, `settings-api`, `render-api`, `limits` |
| `RenderLine(from, to, color, thickness)` | `render-api`, `limits` |
| `RenderCircle(position, radius, color, thickness, segments)` | `render-api` |
| `RenderCircleFilled(position, radius, color, segments)` | `render-api` |
| `RenderRect(from, to, color, rounding, roundingCornersFlags, thickness)` | `render-api` |
| `RenderRectFilled(from, to, color, rounding, roundingCornersFlags)` | `render-api` |
| `IsWorldPosOnScreen(worldPos)` | `render-api`, `limits` |
| `WorldToScreen(worldPos)` | `render-api`, `limits` |
| `WorldToMinimap(worldPos)` | `render-api`, `limits` |
| `GetZoom()` | `render-api`, `limits` |
| `GetCameraPosition()` | `types`, `render-api`, `limits` |
| `RenderWorldLine(from, to, color, thickness)` | `render-api` |
| `RenderWorldRect(worldPos, width, height, color, thickness)` | `render-api` |
| `RenderWorldRectFilled(worldPos, width, height, color)` | `render-api` |
| `RenderWorldCircle(worldPos, radius, color, thickness, segments)` | `render-api`, `limits` |
| `RenderWorldCircleFilled(worldPos, radius, color, segments)` | `render-api` |
| `RenderWorldText(text, worldPos, size, color, center, border)` | `types`, `render-api` |
| `RenderObjectBounds(object, color, thickness)` | `facts`, `render-api` |
| `RenderObjectBoundsFilled(object, color)` | `render-api` |
| `RenderMinimapDot(worldPos, radius, color)` | `render-api` |
| `RenderMinimapLine(worldPosFrom, worldPosTo, thickness, color)` | `render-api` |
| `RenderMinimapRect(worldPos, width, height, color, thickness)` | `render-api` |
| `RenderMinimapRectFilled(worldPos, width, height, color)` | `render-api` |
| `IsKeyPressed(vkCode)` | `enums`, `settings-api` |
| `ParseJSON(str)` | `ipc-api` |
| `ToJSON(obj)` | `ipc-api` |
| `GetRandomMapControlCapabilities()` | `limits`, `session-control`, `game-options` |
| `GetRandomMapStartStatus()` | `limits`, `session-control` |
| `RefreshRandomMapSources()` | `limits`, `session-control`, `game-options` |
| `GetAvailableRandomMapSources()` | `limits`, `session-control`, `game-options` |
| `GetEffectiveRandomMapSeed()` | `limits`, `session-control` |
| `GetEffectiveRandomMapSource()` | `limits`, `session-control` |

## Vector2 (10)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Vector2.new(x, y)` | `types` |
| `Vector2:LengthSqr()` | Não encontrado por busca literal |
| `Vector2:Length()` | Não encontrado por busca literal |
| `Vector2:Normalize()` | Não encontrado por busca literal |
| `Vector2:Normalized()` | Não encontrado por busca literal |
| `Vector2:Dot(other)` | Não encontrado por busca literal |
| `Vector2:Cross(other)` | Não encontrado por busca literal |
| `Vector2:IsNearlyZero()` | Não encontrado por busca literal |
| `Vector2:Lerp(target, alpha)` | Não encontrado por busca literal |
| `Vector2:Distance(other)` | Não encontrado por busca literal |

## Vector3 (10)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Vector3.new(x, y, z)` | `types` |
| `Vector3:LengthSqr()` | Não encontrado por busca literal |
| `Vector3:Length()` | Não encontrado por busca literal |
| `Vector3:Normalize()` | Não encontrado por busca literal |
| `Vector3:Normalized()` | Não encontrado por busca literal |
| `Vector3:Dot(other)` | Não encontrado por busca literal |
| `Vector3:Cross(other)` | Não encontrado por busca literal |
| `Vector3:IsNearlyZero()` | Não encontrado por busca literal |
| `Vector3:Lerp(target, alpha)` | Não encontrado por busca literal |
| `Vector3:Distance(other)` | Não encontrado por busca literal |

## Vector4 (9)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Vector4.new(x, y, z, w)` | `types` |
| `Vector4:LengthSqr()` | Não encontrado por busca literal |
| `Vector4:Length()` | Não encontrado por busca literal |
| `Vector4:Normalize()` | Não encontrado por busca literal |
| `Vector4:Normalized()` | Não encontrado por busca literal |
| `Vector4:Dot(other)` | Não encontrado por busca literal |
| `Vector4:IsNearlyZero()` | Não encontrado por busca literal |
| `Vector4:Lerp(target, alpha)` | Não encontrado por busca literal |
| `Vector4:Distance(other)` | Não encontrado por busca literal |

## Color (3)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Color.new(r, g, b, a)` | `types` |
| `Color.Parse(hexStr)` | `types` |
| `Color.HSV(h, s, v, a)` | `types` |

## GameOptions (66)

| Assinatura | Páginas contendo o nome |
|---|---|
| `GameOptions:GetAIDifficulty()` | Não encontrado por busca literal |
| `GameOptions:SetAIDifficulty(difficulty)` | Não encontrado por busca literal |
| `GameOptions:GetCivilizationSet()` | Não encontrado por busca literal |
| `GameOptions:SetCivilizationSet(civilizationSet)` | Não encontrado por busca literal |
| `GameOptions:GetGameMode()` | Não encontrado por busca literal |
| `GameOptions:SetGameMode(gameMode)` | Não encontrado por busca literal |
| `GameOptions:GetMapSize()` | Não encontrado por busca literal |
| `GameOptions:SetMapSize(mapSize)` | Não encontrado por busca literal |
| `GameOptions:GetStartingAge()` | Não encontrado por busca literal |
| `GameOptions:SetStartingAge(age)` | Não encontrado por busca literal |
| `GameOptions:GetEndingAge()` | Não encontrado por busca literal |
| `GameOptions:SetEndingAge(age)` | Não encontrado por busca literal |
| `GameOptions:GetGameSpeed()` | Não encontrado por busca literal |
| `GameOptions:SetGameSpeed(gameSpeed)` | Não encontrado por busca literal |
| `GameOptions:GetRevealMap()` | Não encontrado por busca literal |
| `GameOptions:SetRevealMap(revealMap)` | Não encontrado por busca literal |
| `GameOptions:GetVictory()` | Não encontrado por busca literal |
| `GameOptions:SetVictory(victory)` | Não encontrado por busca literal |
| `GameOptions:GetVictoryLimit()` | Não encontrado por busca literal |
| `GameOptions:SetVictoryLimit(victoryLimit)` | Não encontrado por busca literal |
| `GameOptions:GetResources()` | Não encontrado por busca literal |
| `GameOptions:SetResources(resources)` | Não encontrado por busca literal |
| `GameOptions:GetPopulation()` | Não encontrado por busca literal |
| `GameOptions:SetPopulation(population)` | Não encontrado por busca literal |
| `GameOptions:GetTeamsNotTogether()` | Não encontrado por busca literal |
| `GameOptions:SetTeamsNotTogether(teamsNotTogether)` | Não encontrado por busca literal |
| `GameOptions:GetRecordGame()` | Não encontrado por busca literal |
| `GameOptions:SetRecordGame(recordGame)` | Não encontrado por busca literal |
| `GameOptions:GetTeamPositions()` | Não encontrado por busca literal |
| `GameOptions:SetTeamPositions(teamPositions)` | Não encontrado por busca literal |
| `GameOptions:GetFullTechTree()` | Não encontrado por busca literal |
| `GameOptions:SetFullTechTree(fullTechTree)` | Não encontrado por busca literal |
| `GameOptions:GetLockTeams()` | Não encontrado por busca literal |
| `GameOptions:SetLockTeams(lockTeams)` | Não encontrado por busca literal |
| `GameOptions:GetLockSpeed()` | Não encontrado por busca literal |
| `GameOptions:SetLockSpeed(lockSpeed)` | Não encontrado por busca literal |
| `GameOptions:GetTurboMode()` | Não encontrado por busca literal |
| `GameOptions:SetTurboMode(turboMode)` | Não encontrado por busca literal |
| `GameOptions:GetAntiquityMode()` | Não encontrado por busca literal |
| `GameOptions:SetAntiquityMode(antiquityMode)` | Não encontrado por busca literal |
| `GameOptions:GetLocation()` | Não encontrado por busca literal |
| `GameOptions:SetLocation(location)` | Não encontrado por busca literal |
| `GameOptions:SetRandomMapPoolLocations(locations)` | Não encontrado por busca literal |
| `GameOptions:GetRandomMapSeed()` | Não encontrado por busca literal |
| `GameOptions:SetRandomMapSeed(seed)` | Não encontrado por busca literal |
| `GameOptions:ClearRandomMapSeed()` | Não encontrado por busca literal |
| `GameOptions:GetRandomMapSource()` | Não encontrado por busca literal |
| `GameOptions:SetRandomMapSource(source)` | Não encontrado por busca literal |
| `GameOptions:GetPlayersCount()` | Não encontrado por busca literal |
| `GameOptions:SetPlayersCount(playersCount)` | Não encontrado por busca literal |
| `GameOptions:GetTreatyLength()` | Não encontrado por busca literal |
| `GameOptions:SetTreatyLength(treatyLength)` | Não encontrado por busca literal |
| `GameOptions:GetHandicap()` | Não encontrado por busca literal |
| `GameOptions:SetHandicap(handicap)` | Não encontrado por busca literal |
| `GameOptions:GetPlayerTeam(playerIndex)` | Não encontrado por busca literal |
| `GameOptions:SetPlayerTeam(playerIndex, team)` | Não encontrado por busca literal |
| `GameOptions:GetPlayerHandicapPercentage(playerIndex)` | Não encontrado por busca literal |
| `GameOptions:SetPlayerHandicapPercentage(playerIndex, handicapPercentage)` | Não encontrado por busca literal |
| `GameOptions:GetPlayerColor(playerIndex)` | Não encontrado por busca literal |
| `GameOptions:SetPlayerColor(playerIndex, color)` | Não encontrado por busca literal |
| `GameOptions:GetPlayerCivilization(playerIndex)` | Não encontrado por busca literal |
| `GameOptions:SetPlayerCivilization(playerIndex, civilization)` | Não encontrado por busca literal |
| `GameOptions:SetAssignedPlayerCivilization(civilization)` | Não encontrado por busca literal |
| `GameOptions:GetPlayerAI(playerIndex)` | Não encontrado por busca literal |
| `GameOptions:SetPlayerAI(playerIndex, name)` | Não encontrado por busca literal |
| `GameOptions:GetAvailableAIs()` | Não encontrado por busca literal |

## MapTile (9)

| Assinatura | Páginas contendo o nome |
|---|---|
| `MapTile:GetPosition()` | Não encontrado por busca literal |
| `MapTile:GetTerrain()` | `enums` |
| `MapTile:GetElevation()` | Não encontrado por busca literal |
| `MapTile:GetTileVisibility()` | `enums` |
| `MapTile:IsBuildable()` | `facts`, `limits` |
| `MapTile:IsWalkable()` | `facts`, `limits` |
| `MapTile:IsNavigatable()` | Não encontrado por busca literal |
| `MapTile:GetObjectCount()` | Não encontrado por busca literal |
| `MapTile:GetObjects()` | `types` |

## Object (29)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Object:GetId()` | Não encontrado por busca literal |
| `Object:GetName()` | Não encontrado por busca literal |
| `Object:GetGraphicFileName()` | Não encontrado por busca literal |
| `Object:GetTypeName()` | Não encontrado por busca literal |
| `Object:GetObjectType()` | `enums` |
| `Object:GetOwningPlayer()` | `types` |
| `Object:GetGarrisonObject()` | Não encontrado por busca literal |
| `Object:GetTargetPosition()` | Não encontrado por busca literal |
| `Object:GetActionTargetPosition()` | Não encontrado por busca literal |
| `Object:GetTargetObject()` | Não encontrado por busca literal |
| `Object:GetDirection()` | Não encontrado por busca literal |
| `Object:GetPosition()` | `render-api` |
| `Object:GetCurrentMapTile()` | `types` |
| `Object:GetHitpoints()` | Não encontrado por busca literal |
| `Object:GetMaxHitpoints()` | Não encontrado por busca literal |
| `Object:IsAlive()` | Não encontrado por busca literal |
| `Object:IsFoundation()` | Não encontrado por busca literal |
| `Object:GetUnitObjectType()` | Não encontrado por busca literal |
| `Object:GetClass()` | Não encontrado por busca literal |
| `Object:GetAttribute(attribute, damageType)` | `enums`, `limits` |
| `Object:GetObjectData(objectData)` | `enums`, `limits` |
| `Object:GetPath()` | Não encontrado por busca literal |
| `Object:CalculatePath(targetPos)` | `facts`, `limits` |
| `Object:IsIdle()` | Não encontrado por busca literal |
| `Object:IsMoving()` | Não encontrado por busca literal |
| `Object:GetSprite()` | `types` |
| `Object:IsScouting()` | Não encontrado por busca literal |
| `Object:IsVisible()` | Não encontrado por busca literal |
| `Object:IsExplored()` | Não encontrado por busca literal |

## Player (39)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Player:GetId()` | Não encontrado por busca literal |
| `Player:GetPlayerType()` | `enums` |
| `Player:GetPlayerObjects()` | Não encontrado por busca literal |
| `Player:GetCameraPosition()` | Não encontrado por busca literal |
| `Player:GetMouseHoveredObject()` | Não encontrado por busca literal |
| `Player:GetSelectedObject()` | Não encontrado por busca literal |
| `Player:GetSelectedObjectCount()` | Não encontrado por busca literal |
| `Player:GetPlayerName()` | Não encontrado por busca literal |
| `Player:GetCivilizationId()` | Não encontrado por busca literal |
| `Player:GetCivilizationName()` | Não encontrado por busca literal |
| `Player:GetColor()` | Não encontrado por busca literal |
| `Player:GetAttribute(attribute)` | `enums` |
| `Player:GetFarmReseedQueue()` | `commands` |
| `Player:GetFishTrapRebuildQueue()` | `commands` |
| `Player:IsAutoFarmReseedEnabled()` | Não encontrado por busca literal |
| `Player:IsAutoFishTrapRebuildEnabled()` | Não encontrado por busca literal |
| `Player:GetGoal(goalId)` | `commands` |
| `Player:GetGoals(firstGoalId, lastGoalId)` | `commands` |
| `Player:GetUnitTypeCount(unitId)` | Não encontrado por busca literal |
| `Player:GetFact(factId, parameter)` | `enums`, `limits` |
| `Player:CanAfford(unitId, isBuilding)` | Não encontrado por busca literal |
| `Player:GetTechCost(technology)` | `enums` |
| `Player:GetObjectCost(unitObjectType, costMultiplier)` | `enums` |
| `Player:IsObjectTypeAvailable(unitObjectType)` | Não encontrado por busca literal |
| `Player:GetResearchState(technology)` | `enums` |
| `Player:CanAffordResearch(technology)` | Não encontrado por busca literal |
| `Player:CanResearch(technology)` | Não encontrado por busca literal |
| `Player:IsTechnologyResearched(technology)` | Não encontrado por busca literal |
| `Player:GetObjectsByTypes(unitTypes)` | Não encontrado por busca literal |
| `Player:GetObjectsByMostCommonType(unitTypes)` | Não encontrado por busca literal |
| `Player:GetObjectsByClass(unitClass)` | `enums` |
| `Player:GetObjectsByClassDeadInclusive(unitClass)` | Não encontrado por busca literal |
| `Player:GetFoundations()` | `facts` |
| `Player:CountObjectsByTypes(unitTypes)` | Não encontrado por busca literal |
| `Player:CountObjectsByClass(unitClass)` | `enums` |
| `Player:GetTownCenters()` | Não encontrado por busca literal |
| `Player:HasWon()` | Não encontrado por busca literal |
| `Player:IsAlliedWith(player)` | Não encontrado por busca literal |
| `Player:IsEnemyTo(player)` | Não encontrado por busca literal |

## Settings (13)

| Assinatura | Páginas contendo o nome |
|---|---|
| `Settings.AddBool(key, default)` | `settings-api` |
| `Settings.AddInt(key, default, min, max)` | `settings-api` |
| `Settings.AddFloat(key, default, min, max)` | `settings-api` |
| `Settings.AddDropdown(key, default, options)` | `settings-api` |
| `Settings.AddKeybind(key, defaultVkCode)` | `enums`, `settings-api` |
| `Settings.AddColor(key, defaultColor)` | `settings-api` |
| `Settings.AddTooltip(key, tooltip)` | `settings-api` |
| `Settings.GetBool(key, default)` | `settings-api` |
| `Settings.GetInt(key, default)` | `settings-api` |
| `Settings.GetFloat(key, default)` | `settings-api` |
| `Settings.GetString(key, default)` | `settings-api` |
| `Settings.GetKeybind(key, defaultVkCode)` | `enums`, `settings-api` |
| `Settings.GetColor(key, defaultColor)` | `settings-api` |

## IPC (7)

| Assinatura | Páginas contendo o nome |
|---|---|
| `IPC.StartServer(pipeName)` | `lifecycle`, `ipc-api` |
| `IPC.StopServer()` | `lifecycle`, `ipc-api` |
| `IPC.Send(message)` | `ipc-api`, `limits` |
| `IPC.HasMessages()` | `ipc-api` |
| `IPC.GetMessages()` | `ipc-api` |
| `IPC.WaitForMessage(timeoutMs)` | `ipc-api`, `limits` |
| `IPC.GetStats()` | `ipc-api` |

## ResourceTracker (10)

| Assinatura | Páginas contendo o nome |
|---|---|
| `ResourceTracker.new(...)` | `types` |
| `ResourceTracker:Update()` | Não encontrado por busca literal |
| `ResourceTracker:GetConvertibleLivestock(position, radius)` | Não encontrado por busca literal |
| `ResourceTracker:GetOwnedLivestock()` | Não encontrado por busca literal |
| `ResourceTracker:GetDeadLivestock(position, radius)` | Não encontrado por busca literal |
| `ResourceTracker:GetTrees()` | Não encontrado por busca literal |
| `ResourceTracker:GetGold()` | Não encontrado por busca literal |
| `ResourceTracker:GetStone()` | Não encontrado por busca literal |
| `ResourceTracker:GetForage()` | Não encontrado por busca literal |
| `ResourceTracker:GetFarms()` | Não encontrado por busca literal |

## VillagerOccupation (19)

| Assinatura | Páginas contendo o nome |
|---|---|
| `VillagerOccupation.new(...)` | `types` |
| `VillagerOccupation:Update()` | Não encontrado por busca literal |
| `VillagerOccupation:GetVillagerCount(profession)` | `enums` |
| `VillagerOccupation:GetIdleVillagerCount()` | Não encontrado por busca literal |
| `VillagerOccupation:GetAllVillagers()` | Não encontrado por busca literal |
| `VillagerOccupation:GetIdleVillagers()` | Não encontrado por busca literal |
| `VillagerOccupation:RequestVillagers(amount, position, urgency)` | `enums` |
| `VillagerOccupation:RebalanceVillagers()` | Não encontrado por busca literal |
| `VillagerOccupation:SetPriorities(wood, food, gold, stone)` | Não encontrado por busca literal |
| `VillagerOccupation:GetPriorityPercentage(profession)` | Não encontrado por busca literal |
| `VillagerOccupation:ResetPriorities()` | Não encontrado por busca literal |
| `VillagerOccupation:SetPriorityPercentage(profession, percentage)` | Não encontrado por busca literal |
| `VillagerOccupation:SetLivestockVillagerLimit(limit)` | Não encontrado por busca literal |
| `VillagerOccupation:SetForageVillagerLimit(limit)` | Não encontrado por busca literal |
| `VillagerOccupation:SetFarmMaxTownCenterDistance(distance)` | Não encontrado por busca literal |
| `VillagerOccupation:SetFarmMaxMillDistance(distance)` | Não encontrado por busca literal |
| `VillagerOccupation:SetProfessionBuildingRange(profession, range)` | Não encontrado por busca literal |
| `VillagerOccupation:AssignVillagers(villagers)` | Não encontrado por busca literal |
| `VillagerOccupation:AssignVillager(villager)` | Não encontrado por busca literal |

## ConstructionPlacement (12)

| Assinatura | Páginas contendo o nome |
|---|---|
| `ConstructionPlacement.new(...)` | `types` |
| `ConstructionPlacement:Update()` | Não encontrado por busca literal |
| `ConstructionPlacement:SetTownCenterPadding(padding)` | Não encontrado por busca literal |
| `ConstructionPlacement:BuildStructure(structureType, builderUnitId, targetPos, direction, padding, bypassTownCenterPadding)` | `enums` |
| `ConstructionPlacement:BuildStructureAtTown(structureType, targetPos, padding, bypassTownCenterPadding)` | Não encontrado por busca literal |
| `ConstructionPlacement:FindBestPosition(structureType, targetPos, direction, padding, bypassTownCenterPadding)` | Não encontrado por busca literal |
| `ConstructionPlacement:GetValidFarmPlacementTile()` | `types` |
| `ConstructionPlacement:QueueBuildingRequest(structureType, targetPosition, priority, padding, bypassTownCenterPadding, builderUnitId, requireScouting)` | `enums` |
| `ConstructionPlacement:QueueBuildingRequestAtTown(structureType, priority, padding, bypassTownCenterPadding, builderUnitId, requireScouting)` | Não encontrado por busca literal |
| `ConstructionPlacement:ProcessBuildingRequests()` | Não encontrado por busca literal |
| `ConstructionPlacement:IsStructureTypeQueued(structureType)` | Não encontrado por busca literal |
| `ConstructionPlacement:IsUnitAssignedToBuilding(unitId)` | Não encontrado por busca literal |

## RandomMapSource (8)

| Assinatura | Páginas contendo o nome |
|---|---|
| `RandomMapSource:GetDisplayName()` | Não encontrado por busca literal |
| `RandomMapSource:GetNativeMapId()` | Não encontrado por busca literal |
| `RandomMapSource:GetSourceKind()` | Não encontrado por busca literal |
| `RandomMapSource:GetModIdentity()` | Não encontrado por busca literal |
| `RandomMapSource:GetResolvedPath()` | Não encontrado por busca literal |
| `RandomMapSource:GetSourceIdentity()` | Não encontrado por busca literal |
| `RandomMapSource:GetAuthoredSourceSha256()` | Não encontrado por busca literal |
| `RandomMapSource:GetCatalogGeneration()` | Não encontrado por busca literal |


## Critérios de transposição HD

- Estado HD: `a_investigar_HD` para todas as assinaturas.
- Nome da função, argumento e retorno observados na DE não confirmam API ou ABI equivalentes na HD.
- Toda descoberta de endereço/identificador deverá ser registrada com evidência no `AoE2HD.mapping`.
- Implementação e testes vão para `AoE2HD.control`.
- Segurança: somente sessões locais/offline; nenhum uso em partidas competitivas online.
