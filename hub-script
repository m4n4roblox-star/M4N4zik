-- MUSIC HUB (version propre)

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local theme = Color3.fromRGB(0, 210, 255)

local Playlist = {
    {genre = "Afro Ori Fiesta", tracks = {
        {Name = "AFRO TORNADO SHIPA 2026", ID = "117161727244578"},
        {Name = "MAKE DE HIT'S Remake", ID = "108586389109295"},
        {Name = "BORA BORA 2 Remake", ID = "132504918306819"},
        {Name = "PANTALON RAI TAHITI Remake", ID = "88356625906917"},
        {Name = "ARO STYLE", ID = "70456289029227"},
        {Name = "KARDASH DE DIA", ID = "71912032385123"},
        {Name = "NUKEA AFRO DROP", ID = "106742335971293"},
        {Name = "AFRO DRIP DE KEN DECK", ID = "73705834856973"},
        {Name = "Mahdjah & DIABLESSE Feat", ID = "124327914096423"},
    }},
    {genre = "Melancholique Chill", tracks = {
        {Name = "BOYCA DIT LE MOI", ID = "88158785743073"},
        {Name = "Zook Azog lunery (remake)", ID = "79105403930715"},
        {Name = "PETIT CŒUR", ID = "86088146219404"},
        {Name = "SOUVENIR BOYCA", ID = "94964313790233"},
        {Name = "REVIENS MOI", ID = "101783626338367"},
        {Name = "SAXKROM R.I.P", ID = "111817098972864"},
        {Name = "Bon bon à la menth remix", ID = "101631490058652"},
        {Name = "Obliger de t'aimer BOYCA", ID = "105889258873636"},
        {Name = "Gardienne de mon cœur", ID = "105894702939451"},
        {Name = "Sirenaa Deck", ID = "81546712632241"},
        {Name = "Sirenaa Zook", ID = "109300587199011"},
        {Name = "Saxo maker's JR", ID = "70729137127169"},
        {Name = "Dernière DANSE", ID = "92575425026398"},
    }},
    {genre = "Deck PSYCHO", tracks = {
        {Name = "ITS NOT ME AZCROW", ID = "95964893831245"},
        {Name = "SYCKROW COME BACK DU SAX", ID = "125083785589706"},
        {Name = "SOY EL FUEGO", ID = "114763201016615"},
        {Name = "PAPARA STREET 39", ID = "96015965794739"},
    }},
}

local function new(class, props, parent)
    local o = Instance.new(class)
    for k, v in pairs(props) do o[k] = v end
    o.Parent = parent
    return o
end

local function corner(o, r)
    new("UICorner", {CornerRadius = UDim.new(0, r)}, o)
end

local function getGuiParent()
    local ok, h = pcall(function() return gethui and gethui() end)
    if ok and h then return h end
    local ok2 = pcall(function() return game:GetService("CoreGui"):GetChildren() end)
    if ok2 then return game:GetService("CoreGui") end
    return Players.LocalPlayer:WaitForChild("PlayerGui")
end

local guiParent = getGuiParent()
local old = guiParent:FindFirstChild("MusicHub_Clean")
if old then old:Destroy() end

local ScreenGui = new("ScreenGui", {Name = "MusicHub_Clean", ResetOnSpawn = false}, guiParent)

local Main = new("Frame", {
    Size = UDim2.new(0, 560, 0, 340),
    Position = UDim2.new(0.5, -280, 0.5, -170),
    BackgroundColor3 = Color3.fromRGB(12, 12, 16),
    Active = true,
    Draggable = true,
}, ScreenGui)
corner(Main, 12)
local MainStroke = new("UIStroke", {Color = theme, Thickness = 1.5}, Main)

local Title = new("TextLabel", {
    Size = UDim2.new(1, -70, 0, 28),
    Position = UDim2.new(0, 16, 0, 6),
    BackgroundTransparency = 1,
    Text = "🎵 Music Hub",
    TextColor3 = theme,
    Font = Enum.Font.Code,
    TextSize = 20,
    TextXAlignment = Enum.TextXAlignment.Left,
}, Main)

local Status = new("TextLabel", {
    Size = UDim2.new(1, -70, 0, 16),
    Position = UDim2.new(0, 16, 0, 34),
    BackgroundTransparency = 1,
    Text = "Choisis une musique",
    TextColor3 = Color3.fromRGB(140, 140, 150),
    Font = Enum.Font.SourceSansItalic,
    TextSize = 13,
    TextXAlignment = Enum.TextXAlignment.Left,
}, Main)

local MinBtn = new("TextButton", {
    Size = UDim2.new(0, 32, 0, 32),
    Position = UDim2.new(1, -44, 0, 8),
    BackgroundColor3 = Color3.fromRGB(24, 24, 30),
    Text = "—",
    TextColor3 = Color3.fromRGB(200, 200, 200),
    Font = Enum.Font.SourceSansBold,
    TextSize = 16,
}, Main)
corner(MinBtn, 6)

local Icon = new("TextButton", {
    Size = UDim2.new(0, 52, 0, 52),
    Position = UDim2.new(0.05, 0, 0.2, 0),
    BackgroundColor3 = Color3.fromRGB(15, 15, 20),
    Text = "🎵",
    TextSize = 24,
    Visible = false,
    Active = true,
    Draggable = true,
}, ScreenGui)
corner(Icon, 26)
local IconStroke = new("UIStroke", {Color = theme, Thickness = 2}, Icon)

MinBtn.MouseButton1Click:Connect(function()
    Main.Visible = false
    Icon.Visible = true
end)
Icon.MouseButton1Click:Connect(function()
    Main.Visible = true
    Icon.Visible = false
end)

local Search = new("TextBox", {
    Size = UDim2.new(0, 150, 0, 28),
    Position = UDim2.new(0, 12, 0, 58),
    BackgroundColor3 = Color3.fromRGB(22, 22, 28),
    PlaceholderText = "🔍 Rechercher...",
    PlaceholderColor3 = Color3.fromRGB(100, 100, 120),
    Text = "",
    TextColor3 = Color3.fromRGB(220, 220, 220),
    Font = Enum.Font.SourceSans,
    TextSize = 13,
    ClearTextOnFocus = false,
}, Main)
corner(Search, 6)

local Nav = new("ScrollingFrame", {
    Size = UDim2.new(0, 150, 1, -100),
    Position = UDim2.new(0, 12, 0, 92),
    BackgroundColor3 = Color3.fromRGB(18, 18, 24),
    BorderSizePixel = 0,
    ScrollBarThickness = 3,
    CanvasSize = UDim2.new(0, 0, 0, 0),
    AutomaticCanvasSize = Enum.AutomaticSize.Y,
}, Main)
corner(Nav, 6)
new("UIListLayout", {Padding = UDim.new(0, 5)}, Nav)

local Content = new("Frame", {
    Size = UDim2.new(1, -184, 1, -66),
    Position = UDim2.new(0, 172, 0, 58),
    BackgroundTransparency = 1,
}, Main)

local function clearContent()
    for _, c in ipairs(Content:GetChildren()) do c:Destroy() end
end

local function jouer(id, nom)
    local RE = ReplicatedStorage:FindFirstChild("RE")
    if not RE then
        Status.Text = "⚠ Remotes introuvables (jeu non compatible)"
        return
    end

    pcall(function()
        local r1 = RE:FindFirstChild("1NoMoto1rVehicle1s")
        if r1 then r1:FireServer("PickingScooterMusicText", tostring(id), true) end

        local r2 = RE:FindFirstChild("1Player1sCa1r")
        if r2 then r2:FireServer("PickingVehicleMusicText", tostring(id), true) end

        local r3 = RE:FindFirstChild("PlayerToolEvent")
        if r3 then r3:FireServer("ToolMusicText", tostring(id), nil, true) end
    end)

    Status.Text = "▶ " .. nom
end

local function afficherPistes(liste)
    clearContent()
    local scroll = new("ScrollingFrame", {
        Size = UDim2.new(1, 0, 1, 0),
        BackgroundTransparency = 1,
        BorderSizePixel = 0,
        ScrollBarThickness = 4,
        CanvasSize = UDim2.new(0, 0, 0, 0),
        AutomaticCanvasSize = Enum.AutomaticSize.Y,
    }, Content)
    new("UIListLayout", {Padding = UDim.new(0, 5)}, scroll)

    for _, t in ipairs(liste) do
        local b = new("TextButton", {
            Size = UDim2.new(1, -8, 0, 34),
            BackgroundColor3 = Color3.fromRGB(24, 24, 30),
            Text = "   ▶  " .. t.Name,
            TextColor3 = Color3.fromRGB(220, 220, 220),
            Font = Enum.Font.SourceSans,
            TextSize = 14,
            TextXAlignment = Enum.TextXAlignment.Left,
        }, scroll)
        corner(b, 5)
        b.MouseButton1Click:Connect(function() jouer(t.ID, t.Name) end)
    end
end

local function pageCustom()
    clearContent()
    local box = new("TextBox", {
        Size = UDim2.new(1, -20, 0, 42),
        Position = UDim2.new(0, 10, 0, 16),
        BackgroundColor3 = Color3.fromRGB(22, 22, 28),
        PlaceholderText = "Colle ton ID audio Roblox ici...",
        Text = "",
        TextColor3 = Color3.fromRGB(255, 255, 255),
        Font = Enum.Font.SourceSansBold,
        TextSize = 15,
        ClearTextOnFocus = false,
    }, Content)
    corner(box, 6)

    local btn = new("TextButton", {
        Size = UDim2.new(1, -20, 0, 38),
        Position = UDim2.new(0, 10, 0, 70),
        BackgroundColor3 = Color3.fromRGB(30, 30, 38),
        Text = "Lancer la musique",
        TextColor3 = theme,
        Font = Enum.Font.SourceSansBold,
        TextSize = 15,
    }, Content)
    corner(btn, 6)

    btn.MouseButton1Click:Connect(function()
        local id = box.Text:gsub("%D", "")
        if id ~= "" then jouer(id, "ID perso : " .. id) end
    end)
end

local function pagePalette()
    clearContent()
    new("TextLabel", {
        Size = UDim2.new(1, 0, 0, 26),
        BackgroundTransparency = 1,
        Text = "Couleur néon de l'interface :",
        TextColor3 = Color3.fromRGB(200, 200, 200),
        Font = Enum.Font.SourceSansItalic,
        TextSize = 14,
    }, Content)

    local couleurs = {
        {"Bleu Néon", Color3.fromRGB(0, 210, 255)},
        {"Rouge Impérial", Color3.fromRGB(255, 60, 60)},
        {"Vert Toxique", Color3.fromRGB(60, 255, 110)},
        {"Rose Fuchsia", Color3.fromRGB(255, 20, 160)},
        {"Jaune Éclair", Color3.fromRGB(255, 215, 0)},
    }

    for i, c in ipairs(couleurs) do
        local b = new("TextButton", {
            Size = UDim2.new(1, -20, 0, 34),
            Position = UDim2.new(0, 10, 0, 30 + (i - 1) * 40),
            BackgroundColor3 = Color3.fromRGB(24, 24, 30),
            Text = c[1],
            TextColor3 = c[2],
            Font = Enum.Font.SourceSansBold,
            TextSize = 14,
        }, Content)
        corner(b, 5)
        b.MouseButton1Click:Connect(function()
            theme = c[2]
            MainStroke.Color = c[2]
            IconStroke.Color = c[2]
            Title.TextColor3 = c[2]
        end)
    end
end

local function navBtn(texte, couleur, fond, action)
    local b = new("TextButton", {
        Size = UDim2.new(1, -6, 0, 36),
        BackgroundColor3 = fond,
        Text = texte,
        TextColor3 = couleur,
        Font = Enum.Font.SourceSansBold,
        TextSize = 13,
    }, Nav)
    corner(b, 5)
    b.MouseButton1Click:Connect(action)
end

for _, g in ipairs(Playlist) do
    navBtn(g.genre, Color3.fromRGB(170, 170, 185), Color3.fromRGB(26, 26, 32), function()
        Search.Text = ""
        afficherPistes(g.tracks)
    end)
end
navBtn("✍️ Custom ID", Color3.fromRGB(255, 190, 80), Color3.fromRGB(38, 28, 26), pageCustom)
navBtn("🎨 Palette UI", Color3.fromRGB(90, 255, 140), Color3.fromRGB(26, 36, 30), pagePalette)

Search:GetPropertyChangedSignal("Text"):Connect(function()
    local q = Search.Text:lower()
    if q == "" then
        afficherPistes(Playlist[1].tracks)
        return
    end
    local trouve = {}
    for _, g in ipairs(Playlist) do
        for _, t in ipairs(g.tracks) do
            if t.Name:lower():find(q, 1, true) then
                table.insert(trouve, t)
            end
        end
    end
    afficherPistes(trouve)
end)

afficherPistes(Playlist[1].tracks)
