-- SETTINGS
local systemenabled = script.SystemEnabled.Value
local randomfires = script.RandomFires.Value
local firenotification = script.FireNotification.Value
local mintimefire = script.MinTimeFire.Value
local maxtimefire = script.MaxTimeFire.Value
local collectparttime = script.CollectFirePartsWaitTime.Value
-- DO NOT TOUCH UNDER
local value = math.random(mintimefire,maxtimefire)
local val = math.random(10,20)
print(value)
local fires = script.FirePoints:GetChildren()
local firechosen = fires[math.random(#fires)]
local isfire = false
local event = game.ReplicatedStorage.FireDetection


print("[LUATECH]: LUATECH ENABLED, LOADING SETTINGS:")


if systemenabled == true then
	print("[LUATECH]: SYSTEM IS ENABLED")
else
	print("[LUATECH]: SYSTEM IS DISABLED, DESTROYING SYSTEM!")
	script:Destroy()
end

if randomfires == true then
	print("[LUATECH]: FIRES ARE ENABLED")
elseif randomfires == false or systemenabled == false then
	print("[LUATECH]: FIRES ARE DISABLED")

end
if firenotification == true then
	print("[LUATECH]: FIRE NOTIFICATIONS ARE ENABLED")
elseif firenotification == false then
	print("[LUATECH]: FIRE NOTIFICATIONS ARE DISABLED")

end



while true do
	wait(collectparttime)
	local newvalue = math.random(mintimefire,maxtimefire)
	local newval = math.random(25,45)
	print(newvalue)
	local newfires = script.FirePoints:GetChildren()
	local newfirechosen = newfires[math.random(#newfires)]
	local isfire = false
	if randomfires == true then
		print("[LUATECH]: "..newfirechosen.Name.." is on fire next!")
		wait(value)
		fire = Instance.new("Fire")
		fire.Size = 60
		fire.Parent = newfirechosen
		print("[LUATECH]: "..newfirechosen.Name.." is on fire!")
		if firenotification == true then
			event:Fire()
		else
			return
		end
		
	else
		break
		

	end
end





randomfires.Touched:Connect(function(hit)
	if hit:FindFirstChild("ParticleEmitter") or ("Nozzle") then
		print("[LUATECH]: Putting out fire!")
		fire.Enabled = false
		wait(val)
		print(val)
		fire.Enabled = true
	end
end)






