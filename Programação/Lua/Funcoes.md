startPatchScan()

function windowCaption()
w=getWindow(getForegroundWindow(), GW_HWNDFIRST)

pid=getOpenedProcessID()

while w and (w~=0) do
  if getWindowProcessID(w)==pid then
    print(w..' - '..getWindowCaption(w)..'('..getWindowClassName(w)..')')

  end
  w=getWindow(w,GW_HWNDNEXT)
end
end

--To get the window title of the opened process, activate the following line.

--windowCaption()
----------------------------------------

if f then f.Destroy() f=nil end

f = createForm()
f.width, f.height = 280,100

lblX = createLabel(f)
lblX.left, lblX.top = 20, 5
lblX.font.size = 14

lblY = createLabel(f)
lblY.left, lblY.top = 20, 25
lblY.font.size = 14

lblX1 = createLabel(f)
lblX1.left, lblX1.top = 20, 45
lblX1.font.size = 14

lblY1 = createLabel(f)
lblY1.left, lblY1.top = 20, 65
lblY1.font.size = 14
----------------------------------------
--Lua Engine visible true
print("Hello")

local Panel = { }

function panelCoord1()
Panel.x1=findWindow(nil,"Lua Engine") --My window handle header is CE "Lua Engine"

m=createMemoryStream()
m.size=16

if executeCodeLocalEx('GetWindowRect',Panel.x1,m.Memory) then
  m.Position=0
  Panel.lft=(m.readDword())
  Panel.tp=(m.readDword())
  Panel.rgt=(m.readDword())
  Panel.btm=(m.readDword())

--If the window position is negative, let's fix it.
  if Panel.lft>4294900000 then Panel.lft=Panel.lft - 4294967296  end
  if Panel.tp>4294900000 then Panel.tp=Panel.tp - 4294967296  end
--Let's compare the values obtained and reach the result of width and height.
  Panel.wdt=tonumber(Panel.rgt) - tonumber(Panel.lft)
  Panel.hgt=tonumber(Panel.btm) - tonumber(Panel.tp)
--There may be some deviations. But the result is approximate.
  --print("left= "..Panel.lft.."\ntop= "..Panel.tp.."\nright= "..Panel.rgt.."\nbottom= "..Panel.btm.."\nheight= "..Panel.hgt.."\nwidth= "..Panel.wdt.."\n")
lblX1.caption = "P.height: "..Panel.hgt.." - P.width: "..Panel.wdt
lblY1.caption = "P.Left: "..Panel.lft.." - P.Top: "..Panel.tp
end
m.destroy()
end

if zT1 then zT1.Destroy() zT1=nil end
 zT1=createTimer()
 zT1.Interval=50
 zT1.Enabled=false

local screenFindx1=Panel.wdt
local  screenFindy1=Panel.hgt

function pnlOnEnter()
 local x,y = getMousePos()
 x2=tonumber(x) - tonumber(Panel.lft)
 y2=tonumber(y) - tonumber(Panel.tp)

 if x2<=0 then x2=0
 elseif y2<=0 then y2=0
 elseif x2>=Panel.wdt then x2=Panel.wdt
 elseif y2>=Panel.hgt then y2=Panel.hgt
 end
 lblX.caption = 'X.pos : '..tostring(x2)
 lblY.caption = 'Y.pos : '..tostring(y2)
end
 zT1.OnTimer=pnlOnEnter

if posKey1 then posKey1.Destroy() posKey1=nil end
posKey1=createHotkey(function() panelCoord1() sleep(200) if zT1.Enabled==false then zT1.Enabled=true
else
zT1.Enabled=false end end, VK_F8)
