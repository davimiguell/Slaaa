local brainrots = workspace.Brainrots
local delayTime = 5

local function teleportarParaBase(player, item)
	local base = workspace:FindFirstChild(player.Name .. "_Base")
	if base and base:IsA("Part") then
		wait(delayTime)
		if item and item.Parent then
			item.CFrame = base.CFrame + Vector3.new(0, 3, 0)
		end
	end
end

for _, brainrot in pairs(brainrots:GetChildren()) do
	if brainrot:IsA("Part") then
		brainrot.Touched:Connect(function(hit)
			local character = hit.Parent
			local player = game.Players:GetPlayerFromCharacter(character)
			if player then
				teleportarParaBase(player, brainrot)
			end
		end)
	end
end
