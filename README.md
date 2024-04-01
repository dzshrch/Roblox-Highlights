local character = script.Parent.Parent.Parent -- assuming this script is inside a character

local function highlightPlayer(isHighlighted)
  local highlight = character:FindFirstChild("Highlight") -- assuming you have a Highlight instance in the character
  if highlight then
    highlight.Enabled = isHighlighted
    highlight.OutlineColor = Color3.fromRGB(255, 255, 255) -- white outline
    highlight.OutlineTransparency = if isHighlighted then 0 else 1 end -- transparent when not highlighted
  end
end

local function loopHighlight()
  highlightPlayer(true) -- highlight the player
  wait(5) -- wait for 5 seconds
  highlightPlayer(false) -- remove highlight
end

-- call the loop function initially
loopHighlight()

-- loop the function every 5 seconds
game:GetService("RunService").Heartbeat:Connect(loopHighlight)
