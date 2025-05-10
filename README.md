--Text above head

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")

local JusticeLabel = Instance.new("BillboardGui", HumanoidRootPart)
JusticeLabel.Size = UDim2.new(8, 0, 3, 0)
JusticeLabel.StudsOffset = Vector3.new(0, 4, 0)
JusticeLabel.AlwaysOnTop = true

local JusticeText = Instance.new("TextLabel", JusticeLabel)
JusticeText.Size = UDim2.new(1, 0, 1, 0)
JusticeText.BackgroundTransparency = 1
JusticeText.Text = "Strongest In History"
JusticeText.TextColor3 = Color3.new(255, 0, 0)
JusticeText.TextScaled = true
JusticeText.Font = Enum.Font.Arial

-- End of text

--Avatar Remover

local hair = game.Players.LocalPlayer.Character.FakeHead
hair:Destroy()

-- end of avatar remover

-- Idle Script Credits to Beluganiki for giving me it

local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local Humanoid = Character:WaitForChild("Humanoid")
local RunService = game:GetService("RunService")

local AnimHandler = loadstring(game:HttpGet("https://raw.githubusercontent.com/ProudNamed/SuperLightning/refs/heads/main/AnimModule/MainModule"))()
local Walk = game:GetObjects("rbxassetid://18272422072")[1]
Walk.Parent = Character

game:GetService("ContentProvider"):PreloadAsync({Walk})

local WalkAnim = AnimHandler.new(Character, Walk)
local isPlaying = false


local BlockAnimIds = {
	["rbxassetid://135104210400610"] = true, -- Dashid
	["rbxassetid://13370310513"] = true, --m1
	["rbxassetid://13390230973"] = true,--m2
	["rbxassetid://13378751717"] = true,--m3
	["rbxassetid://13378708199"] = true,--m4
	["rbxassetid://18896127525"] = true,-- move 1
	["rbxassetid://15290930205"] = true,-- move 2
	["rbxassetid://17838619895"] = true,-- move 3
	["rbxassetid://100558589307006"] = true,-- move 4
	["rbxassetid://17464923657"] = true,-- Ultactavtion id
	["rbxassetid://14406991505"] = true,--Ult move 1
	["rbxassetid://15983615423"] = true,-- Ult move 2
	["rbxassetid://17861840167"] = true,-- Ult move 3
	["rbxassetid://18459220516"] = true,-- Ult move 4
	["rbxassetid://15943915877"] = true,
	["rbxassetid://10480796021"] = true,
	["rbxassetid://10480793962"] = true,
	["rbxassetid://10491993682"] = true,
	["rbxassetid://10470389827"] = true,
	["rbxassetid://10470104242"] = true,
	["rbxassetid://10503381238"] = true,
	["rbxassetid://16746843881"] = true,
["rbxassetid://13497875049"] = true,
}

local function isBlockefhhjua6dByOtherAnim()
	for _, track in Humanoid:GetPlayingAnimationTracks() do
		if BlockAnimIds[track.Animation.AnimationId] then
			return true
		end
	end
	return false
end

local function updateAnimation()
	local speed = Humanoid.MoveDirection.Magnitude
	local blocked = isBlockedByOtherAnim()

	if speed == 0 and not isPlaying and not blocked then
		WalkAnim:Play()
		isPlaying = true
	elseif (speed > 0 or blocked) and isPlaying then
		WalkAnim:Stop()
		isPlaying = false
	end
end

RunService.RenderStepped:Connect(updateAnimation)

Humanoid.AnimationPlayed:Connect(function(track)
	if BlockAnimIds[track.Animation.AnimationId] and isPlaying then
		WalkAnim:Stop()
		isPlaying = false
	end
end)

-- End of idle Scipt

-- Text Script: Credis to deathport

local Title = "Made by"
local Text = "Crisp on Discord"
local ButtonText = "Nice"
local Button2Text = "Nice"
local IconId = "90081080297416"
-- [ [ Toggle/Enable  ] ]
local HaveIcon = true
local HaveButton1 = true
local HaveButton2 = false
local Duration = 6
--[ [ Functions ] ]
local function Button1Code()
-- code here
end

local function Button2Code()
-- code here
end

loadstring(game:HttpGet("https://pastebin.com/raw/FUPBRUuY"))()(Title, Text, ButtonText, Button2Text, IconId, HaveIcon, HaveButton1, HaveButton2, Duration, Button1Code, Button2Code)

-- end of text

-- Tsb spawn Highlight

local H = Instance.new("Highlight")
local AY = Instance.new("ForceField")
AY.Name = "AbsoluteImmortal"
AY.Parent = game.Players.LocalPlayer.Character
AY.Visible = false
H.Name = "IFrames but bootleg"
local Spawn = {}
local FT = game:GetService("TweenService"):Create (H, TweenInfo.new(2.68), {FillTransparency = 1})
local OT = game:GetService("TweenService"):Create (H, TweenInfo.new(2.68), {OutlineTransparency = 1})
H.Parent = game.Players.LocalPlayer.Character
H.FillColor = Color3.fromRGB(255, 0, 0)
H.FillTransparency = 0.4524487257003784
H.OutlineColor = Color3.fromRGB(50, 0, 0)
H.OutlineTransparency = 0.2533392012119293
for _, v in workspace.Map:GetChildren() do
    if v.Name == "SpawnLocation" then
        table.insert(Spawn, v)
    end
end
local d1 = Spawn[math.random(#Spawn)]
game.Players.LocalPlayer.Character.PrimaryPart.CFrame = d1.CFrame * CFrame.new(0, 3, 0)
task.delay(2, function()
FT:Play()
OT:Play()
task.wait(2.68)
H:Destroy()
AY:Destroy()
end)

-- End of Spawn Highlight


--[[Accessory and gear converte func]]  

local AccessorySettings = {
    RemoveOriginalAccessories = true --set true to remove accessories
}

local function DisableCollisions(object)
    if object:IsA("BasePart") then
        object.CanCollide = false
        object.CanTouch = false
        object.CanQuery = false
    end
end

local function AttachAccessories(accessoryTable)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    if AccessorySettings.RemoveOriginalAccessories then
        for _, obj in pairs(character:GetChildren()) do
            if obj:IsA("Accessory") then
                obj:Destroy()
            end
        end
    end

    for _, accessoryData in pairs(accessoryTable) do
        local item = game:GetObjects("rbxassetid://" .. tostring(accessoryData.AssetID))[1]
        if not item then
            warn("Failed to load item with ID: " .. tostring(accessoryData.AssetID))
            return
        end

        --convert
        if item:IsA("Tool") then
            local newAccessory = Instance.new("Accessory")
            local handle = item:FindFirstChildWhichIsA("Part") or item:FindFirstChildWhichIsA("MeshPart")

            if handle then
                handle.Parent = newAccessory
                newAccessory.Parent = character
                newAccessory.Name = "ConvertedAccessory"

                DisableCollisions(handle)

                local targetPart = character:FindFirstChild(accessoryData.AttachTo)
                if targetPart then
                    local weld = Instance.new("Weld")
                    weld.Part0 = targetPart
                    weld.Part1 = handle
                    weld.C0 = CFrame.new(accessoryData.Position) * CFrame.Angles(
                        math.rad(accessoryData.Rotation.X),
                        math.rad(accessoryData.Rotation.Y),
                        math.rad(accessoryData.Rotation.Z)
                    )
                    weld.Parent = targetPart
                end
            end
        else
            item.Parent = character
            local targetPart = character:FindFirstChild(accessoryData.AttachTo)
            if targetPart then
                local attachPart = item:FindFirstChildWhichIsA("MeshPart") or item:FindFirstChildWhichIsA("Part")
                if attachPart then
                    DisableCollisions(attachPart)

                    local weld = Instance.new("Weld")
                    weld.Part0 = targetPart
                    weld.Part1 = attachPart
                    weld.C0 = CFrame.new(accessoryData.Position) * CFrame.Angles(
                        math.rad(accessoryData.Rotation.X),
                        math.rad(accessoryData.Rotation.Y),
                        math.rad(accessoryData.Rotation.Z)
                    )
                    weld.Parent = targetPart
                end
            end
        end
    end
end

--[[ACCESSORIES]]  
local Accessories = {
    {
        AssetID = 18200671915,  --ex Meguna Torso accessory
        AttachTo = "Torso",
        Position = Vector3.new(0, -0.1, 0),
        Rotation = Vector3.new(0, 0, 0)
    },
	{
		AssetID = 130876622540685,  --ex Meguna Head accessory
        AttachTo = "Head",
        Position = Vector3.new(0, 0.4, 0.2),
        Rotation = Vector3.new(0, 180, 0)
	}
}

AttachAccessories(Accessories)

--[[END OF ACCESSORY AND GEAR CONVERTER FUNC]]  

--[[doodoo customization system lool]]  
local PlayerCustomization = {
    EnableSkinToneChange = true, --set false to disable
    SkinTones = {
        Head = "Pastel brown",
        Torso = "Pastel brown",
        LeftArm = "Pastel brown",
        RightArm = "Pastel brown",
        LeftLeg = "White",
        RightLeg = "White"
    }
    
    }

--[[SKFUNC]]  
local function ApplySkinTone()
    if not PlayerCustomization.EnableSkinToneChange then return end
    
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    local bodyParts = {
        Head = "Head",
        Torso = "Torso",
        LeftArm = "Left Arm",
        RightArm = "Right Arm",
        LeftLeg = "Left Leg",
        RightLeg = "Right Leg"
    }

    for partName, skinColor in pairs(PlayerCustomization.SkinTones) do
        local bodyPart = character:FindFirstChild(bodyParts[partName])
        if bodyPart and skinColor then
            bodyPart.BrickColor = BrickColor.new(skinColor)
        end
    end
end
--[[doodoo anti character meshes no touchy pls]]  
local function ResetCharacterMesh()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    if PlayerCustomization.RemoveMeshes then
        for _, obj in pairs(character:GetChildren()) do
            if obj:IsA("CharacterMesh") then
                obj:Destroy()
            end
        end

        local head = character:FindFirstChild("Head")
        if head then
            for _, obj in pairs(head:GetChildren()) do
                if obj:IsA("SpecialMesh") then
                    obj:Destroy()
                end
            end

            local headMesh = Instance.new("SpecialMesh")
            headMesh.MeshType = Enum.MeshType.Head
            headMesh.Scale = PlayerCustomization.HeadSize
            headMesh.Parent = head
        end
    end
end

--[[APPLY WHEN SPAWN!!!!!!!!]]  
local function ApplyPlayerCustomization()
    ApplySkinTone()
    ResetCharacterMesh()
    ApplyClothes()
end

--[[end of doodoo customization system lool]]

-- Clothes script

local char = game.Players.LocalPlayer.Character

pcall(function() char.Pants:Destroy() end)
local v = Instance.new("Pants")
v.Parent = char
v.PantsTemplate = 'rbxassetid://75505491503544'
v.Name = 'Pants'
pcall(function() char.Shirt:Destroy() end)
local v = Instance.new("Shirt")
v.Parent = char
v.ShirtTemplate = 'rbxassetid://120401780245732'
v.Name = 'Shirt'
pcall(function() char['Shirt Graphic']:Destroy() end)
local v = Instance.new("ShirtGraphic")
v.Graphic = 'rbxassetid://3'
v.Name = 'Shirt Graphic'   

-- End of clothes Script


local a=game;local b=a:GetService("Players")
local c=b.LocalPlayer;local d=c:WaitForChild("PlayerGui")
local e=Instance.new("ScreenGui",d)e.Name="WatermarkGui"
local f=Instance.new("TextLabel",e)f.Text="Made by: Crisp on Discord"
f.Size=UDim2.new(0.3,0,0.05,0)f.Position=UDim2.new(0.35,0,0,0)
f.BackgroundTransparency=1;f.TextTransparency=0.5;f.TextSize=13
f.TextColor3=Color3.new(1,1,1)e.ResetOnSpawn=true

--[[Accessory and gear converte func]]  

local AccessorySettings = {
    RemoveOriginalAccessories = true --set true to remove accessories
}

local function DisableCollisions(object)
    if object:IsA("BasePart") then
        object.CanCollide = false
        object.CanTouch = false
        object.CanQuery = false
    end
end

local function AttachAccessories(accessoryTable)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    if AccessorySettings.RemoveOriginalAccessories then
        for _, obj in pairs(character:GetChildren()) do
            if obj:IsA("Accessory") then
                obj:Destroy()
            end
        end
    end

    for _, accessoryData in pairs(accessoryTable) do
        local item = game:GetObjects("rbxassetid://" .. tostring(accessoryData.AssetID))[1]
        if not item then
            warn("Failed to load item with ID: " .. tostring(accessoryData.AssetID))
            return
        end

        --convert
        if item:IsA("Tool") then
            local newAccessory = Instance.new("Accessory")
            local handle = item:FindFirstChildWhichIsA("Part") or item:FindFirstChildWhichIsA("MeshPart")

            if handle then
                handle.Parent = newAccessory
                newAccessory.Parent = character
                newAccessory.Name = "ConvertedAccessory"

                DisableCollisions(handle)

                local targetPart = character:FindFirstChild(accessoryData.AttachTo)
                if targetPart then
                    local weld = Instance.new("Weld")
                    weld.Part0 = targetPart
                    weld.Part1 = handle
                    weld.C0 = CFrame.new(accessoryData.Position) * CFrame.Angles(
                        math.rad(accessoryData.Rotation.X),
                        math.rad(accessoryData.Rotation.Y),
                        math.rad(accessoryData.Rotation.Z)
                    )
                    weld.Parent = targetPart
                end
            end
        else
            item.Parent = character
            local targetPart = character:FindFirstChild(accessoryData.AttachTo)
            if targetPart then
                local attachPart = item:FindFirstChildWhichIsA("MeshPart") or item:FindFirstChildWhichIsA("Part")
                if attachPart then
                    DisableCollisions(attachPart)

                    local weld = Instance.new("Weld")
                    weld.Part0 = targetPart
                    weld.Part1 = attachPart
                    weld.C0 = CFrame.new(accessoryData.Position) * CFrame.Angles(
                        math.rad(accessoryData.Rotation.X),
                        math.rad(accessoryData.Rotation.Y),
                        math.rad(accessoryData.Rotation.Z)
                    )
                    weld.Parent = targetPart
                end
            end
        end
    end
end

--[[ACCESSORIES]]  
local Accessories = {
    {
        AssetID = 18200671915,  --ex Meguna Torso accessory
        AttachTo = "Torso",
        Position = Vector3.new(0, -0.1, 0),
        Rotation = Vector3.new(0, 0, 0)
    },
	{
		AssetID = 130876622540685,  --ex Meguna Head accessory
        AttachTo = "Head",
        Position = Vector3.new(0, 0.4, 0.2),
        Rotation = Vector3.new(0, 180, 0)
	}
}

AttachAccessories(Accessories)

--[[END OF ACCESSORY AND GEAR CONVERTER FUNC]]  

--[[doodoo customization system lool]]  
local PlayerCustomization = {
    EnableSkinToneChange = true, --set false to disable
    SkinTones = {
        Head = "Pastel brown",
        Torso = "Pastel brown",
        LeftArm = "Pastel brown",
        RightArm = "Pastel brown",
        LeftLeg = "White",
        RightLeg = "White"
    },
    RemoveMeshes = false, --NO char meshes (ex: man arm, leg etc)
    HeadSize = Vector3.new(1.25, 1.25, 1.25),
    Clothes = {
        Shirt = nil, --Set to nil to keep default Shirt
        Pants = nil, --Set to nil to keep default Pants
	
        --[[keep in mind you need a clothing (ShirtTemplate or PantsTemplate) to
	use this feature, (you can grab them via btroblox [click on clothing, search
	inside instances and search for respective template] or via roblox studio by
	inserting the clothing, clicking on the instance and copying the id from the
	respective template)]]
    }
}

--[[SKFUNC]]  
local function ApplySkinTone()
    if not PlayerCustomization.EnableSkinToneChange then return end
    
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    local bodyParts = {
        Head = "Head",
        Torso = "Torso",
        LeftArm = "Left Arm",
        RightArm = "Right Arm",
        LeftLeg = "Left Leg",
        RightLeg = "Right Leg"
    }

    for partName, skinColor in pairs(PlayerCustomization.SkinTones) do
        local bodyPart = character:FindFirstChild(bodyParts[partName])
        if bodyPart and skinColor then
            bodyPart.BrickColor = BrickColor.new(skinColor)
        end
    end
end
--[[doodoo anti character meshes no touchy pls]]  
local function ResetCharacterMesh()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    if PlayerCustomization.RemoveMeshes then
        for _, obj in pairs(character:GetChildren()) do
            if obj:IsA("CharacterMesh") then
                obj:Destroy()
            end
        end

        local head = character:FindFirstChild("Head")
        if head then
            for _, obj in pairs(head:GetChildren()) do
                if obj:IsA("SpecialMesh") then
                    obj:Destroy()
                end
            end

            local headMesh = Instance.new("SpecialMesh")
            headMesh.MeshType = Enum.MeshType.Head
            headMesh.Scale = PlayerCustomization.HeadSize
            headMesh.Parent = head
        end
    end
end

--[[CLOTHES]]  
local function ApplyClothes()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    if PlayerCustomization.Clothes.Shirt then
        local shirt = character:FindFirstChildOfClass("Shirt") or Instance.new("Shirt")
        shirt.ShirtTemplate = "rbxassetid://" .. tostring(PlayerCustomization.Clothes.Shirt)
        shirt.Parent = character
    end

    if PlayerCustomization.Clothes.Pants then
        local pants = character:FindFirstChildOfClass("Pants") or Instance.new("Pants")
        pants.PantsTemplate = "rbxassetid://" .. tostring(PlayerCustomization.Clothes.Pants)
        pants.Parent = character
    end
end

--[[APPLY WHEN SPAWN!!!!!!!!]]  
local function ApplyPlayerCustomization()
    ApplySkinTone()
    ResetCharacterMesh()
    ApplyClothes()
end

ApplyPlayerCustomization()
                                                                                               --[[end of doodoo customization system lool]]
                                                                                                local char = game.Players.LocalPlayer.Character

pcall(function() char.Pants:Destroy() end)
local v = Instance.new("Pants")
v.Parent = char
v.PantsTemplate = 'rbxassetid://75505491503544'
v.Name = 'Pants'
pcall(function() char.Shirt:Destroy() end)
local v = Instance.new("Shirt")
v.Parent = char
v.ShirtTemplate = 'rbxassetid://120401780245732'
v.Name = 'Shirt'
pcall(function() char['Shirt Graphic']:Destroy() end)
local v = Instance.new("ShirtGraphic")
v.Graphic = 'rbxassetid://3'
v.Name = 'Shirt Graphic'   

local player = game.Players.LocalPlayer
 
local playerGui = player.PlayerGui
 
local hotbar = playerGui:FindFirstChild("Hotbar")
 
local backpack = hotbar:FindFirstChild("Backpack")
 
local hotbarFrame = backpack:FindFirstChild("Hotbar")
 
local baseButton = hotbarFrame:FindFirstChild("1").Base
 
local ToolName = baseButton.ToolName
 
 
ToolName.Text = "Heavy Black Flash"
 
 
local player = game.Players.LocalPlayer
 
local playerGui = player.PlayerGui
 
local hotbar = playerGui:FindFirstChild("Hotbar")
 
local backpack = hotbar:FindFirstChild("Backpack")
 
local hotbarFrame = backpack:FindFirstChild("Hotbar")
 
local baseButton = hotbarFrame:FindFirstChild("2").Base
 
local ToolName = baseButton.ToolName
 
 
ToolName.Text = "10 Shadow Barrage"
 
 
local player = game.Players.LocalPlayer
 
local playerGui = player.PlayerGui
 
local hotbar = playerGui:FindFirstChild("Hotbar")
 
local backpack = hotbar:FindFirstChild("Backpack")
 
local hotbarFrame = backpack:FindFirstChild("Hotbar")
 
local baseButton = hotbarFrame:FindFirstChild("3").Base
 
local ToolName = baseButton.ToolName
 
 
ToolName.Text = "Cursed Swift Kicker"
 
 
local player = game.Players.LocalPlayer
 
local playerGui = player.PlayerGui
 
local hotbar = playerGui:FindFirstChild("Hotbar")
 
local backpack = hotbar:FindFirstChild("Backpack")
 
local hotbarFrame = backpack:FindFirstChild("Hotbar")
 
local baseButton = hotbarFrame:FindFirstChild("4").Base
 
local ToolName = baseButton.ToolName
 
 
ToolName.Text = "Shadow Stomp Attack"
 
 
local Players = game:GetService("Players")
 
local player = Players.LocalPlayer
 
local playerGui = player:WaitForChild("PlayerGui")
 
 
local function findGuiAndSetText()
 
    local screenGui = playerGui:FindFirstChild("ScreenGui")
 
    if screenGui then
 
        local magicHealthFrame = screenGui:FindFirstChild("MagicHealth")
 
        if magicHealthFrame then
 
            local textLabel = magicHealthFrame:FindFirstChild("TextLabel")
 
            if textLabel then
 
                textLabel.Text = "All 10 Shadows| Strongest in History"
 
            end
 
        end
 
    end
 
end
 
 
playerGui.DescendantAdded:Connect(findGuiAndSetText)
 
findGuiAndSetText()
 
--[[Animations]]
 
--[[Move 1]]
 
local animationId = 10468665991
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://18896127525"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0
 
 
Anim:Play()
 
Anim:AdjustSpeed(1.5)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1.5)
 
    	getgenv().SoundId = "101408037150094"
getgenv().SoundPar = game:GetService("SoundService")
getgenv().RemoveSoundOnEnd = false
getgenv().SoundVolume = 2

local e = Instance.new("Sound")
e.Parent = getgenv().SoundPar
e.SoundId = "rbxassetid://" .. getgenv().SoundId
e.Volume = getgenv().SoundVolume
e:Play()
e.Ended:Connect(function() if getgenv().RemoveSoundOnEnd then e:Destroy() end end)
 
    end
 
end

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10468665991" then
        local Test = game:GetService("ReplicatedStorage").Resources.KJEffects.KJWallCombo.FinalImpact.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(255, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = true
            end
        end
        wait(0.8)
        test:Destroy()
    end
end)

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10468665991" then
        local Test = game.ReplicatedStorage.Resources.NinjaRun.Heavy_Effects.Start.Wide.Second_Shock
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(0, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = true
            end
        end
        wait(0.8)
        test:Destroy()
    end
end)
 
--[[END OF MOVE 1 ANIM]]
 
--[[Move 2]]
 
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local animationId = 10466974800
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://15290930205"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0
 
 
Anim:Play()
 
Anim:AdjustSpeed(1)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1.2)
    	
    	getgenv().SoundId = "5711961181"
getgenv().SoundPar = game:GetService("SoundService")
getgenv().RemoveSoundOnEnd = false
getgenv().SoundVolume = 2

local e = Instance.new("Sound")
e.Parent = getgenv().SoundPar
e.SoundId = "rbxassetid://" .. getgenv().SoundId
e.Volume = getgenv().SoundVolume
e:Play()
e.Ended:Connect(function() if getgenv().RemoveSoundOnEnd then e:Destroy() end end)
 
    end
 
end

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10466974800" then
        local Test = game:GetService("ReplicatedStorage").Resources.AtomicSlash.Floor.Floor.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(255, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = false 
            end
        end
        wait(3)
        test:Destroy()
    end
end)

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10466974800" then
        local Test = game:GetService("ReplicatedStorage").Resources.AtomicSlash.Explosion2.Explosion2.Explosion
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(0, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = false
            end
        end
        wait(3)
        test:Destroy()
    end
end)

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10466974800" then
        local Test = game.ReplicatedStorage.Resources.SplitSecond.CounterLand.Part.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(255, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = true
            end
        end
        wait(1)
        test:Destroy()
    end
end)
 
--[[END OF MOVE 2 ANIM]]
 
--[[Move 3]]
 
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local animationId = 10471336737
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://17838619895"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0.3
 
 
Anim:Play()
 
Anim:AdjustSpeed(0)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1)
 
 
delay(1.8, function()
 
    Anim:Stop()
 
end)
 
    	getgenv().SoundId = "97960256382964"
getgenv().SoundPar = game:GetService("SoundService")
getgenv().RemoveSoundOnEnd = false
getgenv().SoundVolume = 2

local e = Instance.new("Sound")
e.Parent = getgenv().SoundPar
e.SoundId = "rbxassetid://" .. getgenv().SoundId
e.Volume = getgenv().SoundVolume
e:Play()
e.Ended:Connect(function() if getgenv().RemoveSoundOnEnd then e:Destroy() end end)
    	
    end
 
end

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10471336737" then
        local Test = game.ReplicatedStorage.Emotes.VFX.RealAssets["Heart Strike"].Shock.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(255, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = false
            end
        end
        wait(3)
        test:Destroy()
    end
end)

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://10471336737" then
        local Test = game.ReplicatedStorage.Emotes.VFX.RealAssets["To Brazil"].Portall.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then
  
child.Color = ColorSequence.new(Color3.new(0, 0, 0))                                                                                            
child:Emit(15)                                                   
child.Enabled = false
            end
        end
        wait(3)
        test:Destroy()
    end
end)
 
--[[END OF MOVE 3 ANIM]]
 
--[[Move 4]]
 
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local animationId = 12510170988
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://100558589307006"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0
 
 
Anim:Play()
 
Anim:AdjustSpeed(0)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1.5)
 
    	getgenv().SoundId = "103898086385000"
getgenv().SoundPar = game:GetService("SoundService")
getgenv().RemoveSoundOnEnd = false
getgenv().SoundVolume = 3

local e = Instance.new("Sound")
e.Parent = getgenv().SoundPar
e.SoundId = "rbxassetid://" .. getgenv().SoundId
e.Volume = getgenv().SoundVolume
e:Play()
e.Ended:Connect(function() if getgenv().RemoveSoundOnEnd then e:Destroy() end end)
    	
    end
 
end

local Cr = game:GetService("Players")
local Rep = game:GetService("ReplicatedStorage")

local lolskider = Cr.LocalPlayer
local dect = lolskider.Character or lolskider.CharacterAdded:Wait()
local human = dect:WaitForChild("Humanoid")

human.AnimationPlayed:Connect(function(track)
    if track.Animation.AnimationId == "rbxassetid://12510170988" then
        local Test = game.ReplicatedStorage.Resources.RobotStuff.Slam.Slam.Attachment
        local test = Test:Clone()
        test.Parent = dect:WaitForChild("HumanoidRootPart")

        for _, child in ipairs(test:GetChildren()) do
            if child:IsA("ParticleEmitter") then                                                                
child:Emit(15)                                                   
child.Enabled = false
            end
        end
        wait(3)
        test:Destroy()
    end
end)
 
--[[END OF MOVE 4 ANIM]]


--[[Wall combo]]
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
local animationId = 15955393872
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://15943915877"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0.05
 
 
Anim:Play()
 
Anim:AdjustSpeed(0)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1)
 
 
    end
 
end

--[[END OF WALL COMBO ANIM]]
 
--[[Ult Activation]]
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local animationId = 12447707844
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://17464923657"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0
 
 
Anim:Play()
 
Anim:AdjustSpeed(0)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1)
 
    end
 
end
--[[END OF ULT ACTIVATION ANIM]]
 
--[[Dash]]
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local animationId = 10479335397
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local function onAnimationPlayed(animationTrack)
 
    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then
 
local p = game.Players.LocalPlayer
 
local Humanoid = p.Character:WaitForChild("Humanoid")
 
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
 
    animTrack:Stop()
 
end
 
 
local AnimAnim = Instance.new("Animation")
 
AnimAnim.AnimationId = "rbxassetid://135104210400610"
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
 
local startTime = 0
 
 
Anim:Play()
 
Anim:AdjustSpeed(0)
 
Anim.TimePosition = startTime
 
Anim:AdjustSpeed(1.3)
 
 
delay(1.8, function()
 
    Anim:Stop()
 
end)
 
 
    end
 
end
 
--[[END OF DASH ANIM]]
 
--[[Punch anims]]
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local Players = game:GetService("Players")
 
local player = Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoid = character:WaitForChild("Humanoid")
 
 
local animationIdsToStop = {
 
    [17859015788] = true, --downslam finisher
 
    [10469493270] = true, --punch1
 
    [10469630950] = true, --punch2
 
    [10469639222] = true, --punch3
 
    [10469643643] = true, --punch4
 
}
 
 
local replacementAnimations = {
 
    ["10469493270"] = "rbxassetid://13370310513", --punch1
 
    ["10469630950"] = "rbxassetid://13390230973", --punch2
 
    ["10469639222"] = "rbxassetid://13378751717", --punch3
 
    ["10469643643"] = "rbxassetid://13378708199", --punch4
 
    ["17859015788"] = "rbxassetid://12684185971", --downslam finisher
 
    ["11365563255"] = "rbxassetid://14516273501" --punch idk
 
}
 
 
local queue = {}
 
local isAnimating = false
 
 
local function playReplacementAnimation(animationId)
 
    if isAnimating then
 
        table.insert(queue, animationId)
 
        return
 
    end
 
   
 
    isAnimating = true
 
    local replacementAnimationId = replacementAnimations[tostring(animationId)]
 
    if replacementAnimationId then
 
        local AnimAnim = Instance.new("Animation")
 
        AnimAnim.AnimationId = replacementAnimationId
 
        local Anim = humanoid:LoadAnimation(AnimAnim)
 
        Anim:Play()
 
       
 
        Anim.Stopped:Connect(function()
 
            isAnimating = false
 
            if #queue > 0 then
 
                local nextAnimationId = table.remove(queue, 1)
 
                playReplacementAnimation(nextAnimationId)
 
            end
 
        end)
 
    else
 
        isAnimating = false
 
    end
 
end
 
 
local function stopSpecificAnimations()
 
    for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
 
        local animationId = tonumber(track.Animation.AnimationId:match("%d+"))
 
        if animationIdsToStop[animationId] then
 
            track:Stop()
 
        end
 
    end
 
end
 
 
local function onAnimationPlayed(animationTrack)
 
    local animationId = tonumber(animationTrack.Animation.AnimationId:match("%d+"))
 
    if animationIdsToStop[animationId] then
 
        stopSpecificAnimations()
 
        animationTrack:Stop()
 
       
 
        local replacementAnimationId = replacementAnimations[tostring(animationId)]
 
        if replacementAnimationId then
 
            playReplacementAnimation(animationId)
 
        end
 
    end
 
end
 
 
humanoid.AnimationPlayed:Connect(onAnimationPlayed)
 
 
local player = game.Players.LocalPlayer
 
local character = player.Character or player.CharacterAdded:Wait()
 
local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
 
 
local function onBodyVelocityAdded(bodyVelocity)
 
    if bodyVelocity:IsA("BodyVelocity") then
 
        bodyVelocity.Velocity = Vector3.new(bodyVelocity.Velocity.X, 0, bodyVelocity.Velocity.Z)
 
    end
 
end
 
 
character.DescendantAdded:Connect(onBodyVelocityAdded)
 
 
for _, descendant in pairs(character:GetDescendants()) do
 
    onBodyVelocityAdded(descendant)
 
end
 
 
player.CharacterAdded:Connect(function(newCharacter)
 
    character = newCharacter
 
    humanoidRootPart = character:WaitForChild("HumanoidRootPart")
 
    character.DescendantAdded:Connect(onBodyVelocityAdded)
 
   
 
    for _, descendant in pairs(character:GetDescendants()) do
 
        onBodyVelocityAdded(descendant)
 
    end
 
end) 

--[[Execute Anims (Animations when you execute script]]

local p = game.Players.LocalPlayer
local Humanoid = p.Character:WaitForChild("Humanoid")
 
for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do
    animTrack:Stop()
end
 
local AnimAnim = Instance.new("Animation")
AnimAnim.AnimationId = "rbxassetid://16746843881" -- Replace with your animation ID
 
local Anim = Humanoid:LoadAnimation(AnimAnim)
 
local startTime = 0.05
 
Anim:Play()
Anim:AdjustSpeed(0)
Anim.TimePosition = startTime
Anim:AdjustSpeed(1.8)

local sound = Instance.new("Sound")
sound.SoundId = "rbxassetid://7438381072" 
sound.Parent = workspace 

wait(0.50)
        
sound:Play()


sound.Ended:Connect(function()
    sound:Destroy()
end)
 
--[[END OF EXECUTE ANIMS]]

-- Tp Script
local player = game.Players.LocalPlayer
local mouse = player:GetMouse()

local tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Flicker Curse Flash"

local teleportSound = Instance.new("Sound")
teleportSound.SoundId = "rbxassetid://127747836286692"
teleportSound.Volume = 0.8
teleportSound.Name = "TeleportSound"
teleportSound.Parent = tool

local teleportAnim = Instance.new("Animation")
teleportAnim.AnimationId = "rbxassetid://13497875049"

tool.Activated:Connect(function()
    local char = player.Character
    if not char then return end

    local humanoid = char:FindFirstChildOfClass("Humanoid")
    local rootPart = char:FindFirstChild("HumanoidRootPart")
    if not humanoid or not rootPart then return end

    local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
    local animTrack = animator:LoadAnimation(teleportAnim)
    animTrack:Play()

    teleportSound:Play()

    wait(0.2)
    local pos = mouse.Hit.Position + Vector3.new(0, 2.5, 0)
    rootPart.CFrame = CFrame.new(pos)

    local final1 = game.ReplicatedStorage.Resources.Meteor["ExploVar1"].Part.Attachment:Clone()
    final1.Parent = char:FindFirstChild("Torso") or char:FindFirstChild("UpperTorso") or rootPart
    for _, child in ipairs(final1:GetChildren()) do
        if child:IsA("ParticleEmitter") then
            child.Color = ColorSequence.new(Color3.fromRGB(255, 0, 0))
            child:Emit(2)
        end
    end
end)

tool.Parent = player:WaitForChild("Backpack")
