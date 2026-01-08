# Script
On Roblox
-- Script WalkSpeed pour Delta
local nouvelleVitesse = 50
local player = game.Players.LocalPlayer

-- Fonction pour appliquer la vitesse
local function changerVitesse(character)
    local humanoid = character:WaitForChild("Humanoid")
    humanoid.WalkSpeed = nouvelleVitesse
    
    -- Empêche le jeu de remettre la vitesse de base
    humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
        if humanoid.WalkSpeed ~= nouvelleVitesse then
            humanoid.WalkSpeed = nouvelleVitesse
        end
    end)
end

-- Appliquer au personnage actuel
if player.Character then
    changerVitesse(player.Character)
end

-- Appliquer à chaque fois que tu réapparais
player.CharacterAdded:Connect(changerVitesse)

print("Vitesse fixée à " .. nouvelleVitesse)
