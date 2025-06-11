-- Samurai Hub - سكربت بروكهافن بالعربي
-- من تصميم ساموراي ⚔️

local ui = Instance.new("ScreenGui")
ui.Name = "SamuraiHub"
ui.ResetOnSpawn = false
ui.Parent = game.CoreGui

local main = Instance.new("Frame")
main.Size = UDim2.new(0, 350, 0, 280)
main.Position = UDim2.new(0.35, 0, 0.3, 0)
main.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
main.Active = true
main.Draggable = true
main.Parent = ui
main.BorderSizePixel = 0
main.ZIndex = 2

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
title.Font = Enum.Font.GothamBlack
title.Text = "⚔️ ساموراي هاب - بروكهافن"
title.TextColor3 = Color3.fromRGB(255, 0, 0)
title.TextSize = 24
title.Parent = main
title.BorderSizePixel = 0

-- دالة صنع زر
local function makeButton(text, pos, callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 140, 0, 40)
    btn.Position = pos
    btn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    btn.Text = text
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 20
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.BorderSizePixel = 0
    btn.Parent = main
    btn.MouseButton1Click:Connect(callback)
    return btn
end

-- جدول السكنات الجاهزة
local Skins = {
    "Fresh Guy",
    "Cool Dude",
    "Ninja",
    "Casual",
    "Formal",
    "Player"
}

-- نسخ السكن
local copiedSkin = nil

-- زر نسخ السكن
makeButton("نسخ السكن", UDim2.new(0.05, 0, 0.18, 0), function()
    local plr = game.Players.LocalPlayer
    if plr and plr.Character and plr.Character:FindFirstChild("HumanoidDescription") then
        copiedSkin = plr.Character.HumanoidDescription:Clone()
        warn("تم نسخ السكن بنجاح")
    else
        warn("لم أجد سكن للنسخ")
    end
end)

-- زر لصق السكن
makeButton("لصق السكن", UDim2.new(0.55, 0, 0.18, 0), function()
    local plr = game.Players.LocalPlayer
    if copiedSkin then
        plr:ApplyDescription(copiedSkin)
        warn("تم لصق السكن بنجاح")
    else
        warn("لم تقم بنسخ أي سكن")
    end
end)

-- قائمة اختيار السكنات الجاهزة
local dropdownFrame = Instance.new("Frame")
dropdownFrame.Size = UDim2.new(0, 140, 0, 30)
dropdownFrame.Position = UDim2.new(0.05, 0, 0.45, 0)
dropdownFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
dropdownFrame.BorderSizePixel = 0
dropdownFrame.Parent = main

local dropdownText = Instance.new("TextLabel")
dropdownText.Size = UDim2.new(1, 0, 1, 0)
dropdownText.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
dropdownText.Text = "اختيار سكن جاهز ▼"
dropdownText.TextColor3 = Color3.fromRGB(255, 255, 255)
dropdownText.TextSize = 18
dropdownText.Font = Enum.Font.Gotham
dropdownText.Parent = dropdownFrame

local dropdownOpen = false

local dropdownList = Instance.new("Frame")
dropdownList.Size = UDim2.new(0, 140, 0, 0)
dropdownList.Position = UDim2.new(0, 0, 1, 0)
dropdownList.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
dropdownList.BorderSizePixel = 0
dropdownList.ClipsDescendants = true
dropdownList.Parent = dropdownFrame

dropdownText.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dropdownOpen = not dropdownOpen
        if dropdownOpen then
            dropdownList:TweenSize(UDim2.new(0, 140, 0, #Skins * 30), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.3, true)
        else
            dropdownList:TweenSize(UDim2.new(0, 140, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.3, true)
        end
    end
end)

for i, skinName in pairs(Skins) do
    local option = Instance.new("TextButton")
    option.Size = UDim2.new(1, 0, 0, 30)
    option.Position = UDim2.new(0, 0, 0, (i - 1) * 30)
    option.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    option.Text = skinName
    option.TextColor3 = Color3.fromRGB(255, 255, 255)
    option.Font = Enum.Font.Gotham
    option.TextSize = 18
    option.BorderSizePixel = 0
    option.Parent = dropdownList

    option.MouseButton1Click:Connect(function()
        dropdownText.Text = skinName
        dropdownOpen = false
        dropdownList:TweenSize(UDim2.new(0, 140, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.3, true)

        -- تطبيق السكن المختار
        local plr = game.Players.LocalPlayer
        local humanoidDesc = game.Players:GetHumanoidDescriptionFromUserId(plr.UserId)
        if skinName == "Fresh Guy" then
            humanoidDesc = Instance.new("HumanoidDescription")
        elseif skinName == "Cool Dude" then
            humanoidDesc.ClothingColor3 = Color3.fromRGB(0, 0, 255)
            humanoidDesc.HeadColor3 = Color3.fromRGB(255, 224, 189)
        elseif skinName == "Ninja" then
            humanoidDesc.HeadColor3 = Color3.fromRGB(0, 0, 0)
            humanoidDesc.BodyTypeScale = 0.5
        elseif skinName == "Casual" then
            humanoidDesc.ClothingColor3 = Color3.fromRGB(255, 165, 0)
        elseif skinName == "Formal" then
            humanoidDesc.ClothingColor3 = Color3.fromRGB(0, 0, 0)
        elseif skinName == "Player" then
            humanoidDesc = game.Players:GetHumanoidDescriptionFromUserId(plr.UserId)
        end
        plr:ApplyDescription(humanoidDesc)
        warn("تم تطبيق سكن: "..skinName)
    end)
end

-- مشغل الأغاني

local musicFrame = Instance.new("Frame")
musicFrame.Size = UDim2.new(0, 300, 0, 60)
musicFrame.Position = UDim2.new(0.05, 0, 0.7, 0)
musicFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
musicFrame.BorderSizePixel = 0
musicFrame.Parent = main

local musicLabel = Instance.new("TextLabel")
musicLabel.Size = UDim2.new(0.7, 0, 1, 0)
musicLabel.Position = UDim2.new(0, 0, 0, 0)
musicLabel.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
musicLabel.Text = "رابط الأغنية:"
musicLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
musicLabel.TextSize = 18
musicLabel.Font = Enum.Font.Gotham
musicLabel.TextXAlignment = Enum.TextXAlignment.Left
musicLabel.Parent = musicFrame

local musicInput = Instance.new("TextBox")
musicInput.Size = UDim2.new(0.7, 0, 1, 0)
musicInput.Position = UDim2.new(0.3, 0, 0, 0)
musicInput.PlaceholderText = "الصق رابط الأغنية هنا"
musicInput.Text = ""
musicInput.Font = Enum.Font.Gotham
musicInput.TextSize = 18
musicInput.TextColor3 = Color3.fromRGB(255, 255, 255)
musicInput.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
musicInput.ClearTextOnFocus = false
musicInput.Parent = musicFrame

local sound = Instance.new("Sound")
sound.Parent = game.Workspace
sound.Looped = true
sound.Volume = 0.5

makeButton("تشغيل الأغنية", UDim2.new(0.05, 0, 0.85, 0), function()
    local url = musicInput.Text
    if url ~= "" then
        sound.SoundId = "rbxassetid://"..url
        sound:Play()
        warn("بدأ تشغيل الأغنية")
    else
        warn("ادخل رابط صحيح")
    end
end)

makeButton("إيقاف الأغنية", UDim2.new(0.55, 0, 0.85, 0), function()
    sound:Stop()
    warn("تم إيقاف الأغنية
