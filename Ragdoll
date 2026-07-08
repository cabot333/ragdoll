local RagdollModule = {}

function RagdollModule:Ragdoll(char: Model)
	local humanoid = char:FindFirstChildOfClass("Humanoid")
	if humanoid then
		humanoid.PlatformStand = true
	end

	for _, v in pairs(char:GetDescendants()) do
		if v:IsA("Motor6D") then
			local att0 = Instance.new("Attachment")
			local att1 = Instance.new("Attachment")

			att0.CFrame = v.C0
			att1.CFrame = v.C1

			att0.Parent = v.Part0
			att1.Parent = v.Part1

			local socket = Instance.new("BallSocketConstraint")
			socket.Attachment0 = att0
			socket.Attachment1 = att1
			socket.Parent = v.Part0

			socket.LimitsEnabled = true
			socket.TwistLimitsEnabled = true

			v.Enabled = false
		end
	end
end

function RagdollModule:UnRagdoll(char: Model)
	local humanoid = char:FindFirstChildOfClass("Humanoid")
	if humanoid then
		humanoid.PlatformStand = false
	end

	for _, v in pairs(char:GetDescendants()) do
		if v:IsA("BallSocketConstraint") or v:IsA("Attachment") then
			v:Destroy()
		elseif v:IsA("Motor6D") then
			v.Enabled = true
		end
	end
end

function RagdollModule:RagdollForDuration(character: Model, duration: number)
	
	self:Ragdoll(character)
	task.delay(duration, function()
		self:UnRagdoll(character)
	end)
	
end
	
	
return RagdollModule
