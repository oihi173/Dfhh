local player = game.Players.LocalPlayer
local rs = game:GetService("ReplicatedStorage")
local runService = game:GetService("RunService")

local remote = rs:WaitForChild("Valentine2026"):WaitForChild("RemoteEvent")

-- GUI coração simples
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.ResetOnSpawn = false

local btn = Instance.new("TextButton", gui)
btn.Size = UDim2.new(0,50,0,50)
btn.Position = UDim2.new(0.5,-25,0.85,0)
btn.BackgroundColor3 = Color3.fromRGB(255,0,0)
btn.Text = "❤"
btn.TextScaled = true
btn.TextColor3 = Color3.fromRGB(255,255,255)

local ativo = false

btn.MouseButton1Click:Connect(function()
	ativo = not ativo
end)

runService.RenderStepped:Connect(function()
	if ativo then
		remote:FireServer("collect")
	end
end)
