local ReplicatedStorage = game:GetService("ReplicatedStorage")

local adminEvent = Instance.new("RemoteEvent")
adminEvent.Name = "AdminPanelEvent"
adminEvent.Parent = ReplicatedStorage

local ADMINS = {
	[123456789] = true, -- coloque aqui seu UserId
}

adminEvent.OnServerEvent:Connect(function(player, action)
	if not ADMINS[player.UserId] then
		return
	end

	local character = player.Character
	local humanoid = character and character:FindFirstChildOfClass("Humanoid")

	if action == "Money9000T" then
		local leaderstats = player:FindFirstChild("leaderstats")
		local money = leaderstats and leaderstats:FindFirstChild("Money")

		if money then
			money.Value = 9_000_000_000_000
		end

	elseif action == "InfiniteSpeed" then
		if humanoid then
			humanoid.WalkSpeed = 100
		end
	end
end)
