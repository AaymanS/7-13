-----------------------------------------------------------------------------------------
-- Created by: Aayman Shameem
-- Created on: May 15, 2018
-- 
-- This code will take the user to the menu scene
-----------------------------------------------------------------------------------------

local composer = require( "composer" )

display.setStatusBar( display.HiddenStatusBar )

composer.gotoScene( "splashScene" )
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

local composer = require( "composer" )
 
local scene = composer.newScene()
 
-- -----------------------------------------------------------------------------------
-- Code outside of the scene event functions below will only be executed ONCE unless
-- the scene is removed entirely (not recycled) via "composer.removeScene()"
-- -----------------------------------------------------------------------------------

local function showMenuScene()
    local options = {
        effect = "fade",
        time = 500
    }
    composer.gotoScene( "menuScene" , options )
end

-- -----------------------------------------------------------------------------------
-- Scene event functions
-- -----------------------------------------------------------------------------------
 
-- create()
function scene:create( event )
 
    local sceneGroup = self.view
    -- Code here runs when the scene is first created but has not yet appeared on screen
 
end
 
 
-- show()
function scene:show( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is still off screen (but is about to come on screen)
        local background = display.newRect(display.contentCenterX, display.contentCenterY, display.contentWidth, display.contentHeight)
        background:setFillColor( 0,1,1 )
        sceneGroup:insert( background )
        
        local title = display.newText("Splash Scene", display.contentWidth / 2, display.contentHeight / 2, native.systemFont, 48)
        title:setFillColor( 0,0,0 )
        sceneGroup:insert( title )    
        
 
    elseif ( phase == "did" ) then
        -- Code here runs when the scene is entirely on screen
        timer.performWithDelay( 2000, showMenuScene, 1)

    end
end
 
 
-- hide()
function scene:hide( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is on screen (but is about to go off screen)
 
    elseif ( phase == "did" ) then
        -- Code here runs immediately after the scene goes entirely off screen
 
    end
end
 
 
-- destroy()
function scene:destroy( event )
 
    local sceneGroup = self.view
    -- Code here runs prior to the removal of scene's view
 
end
 
 
-- -----------------------------------------------------------------------------------
-- Scene event function listeners
-- -----------------------------------------------------------------------------------
scene:addEventListener( "create", scene )
scene:addEventListener( "show", scene )
scene:addEventListener( "hide", scene )
scene:addEventListener( "destroy", scene )
-- -----------------------------------------------------------------------------------
 
return scene
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

local composer = require( "composer" )
local widget = require( "widget" )
 
local scene = composer.newScene()
 
-- -----------------------------------------------------------------------------------
-- Code outside of the scene event functions below will only be executed ONCE unless
-- the scene is removed entirely (not recycled) via "composer.removeScene()"
-- -----------------------------------------------------------------------------------

local function showGameScene()
    local options = {
        effect = "fade",
        time = 500
    }
    composer.gotoScene( "gameScene" , options )
end 

-- -----------------------------------------------------------------------------------
-- Scene event functions
-- -----------------------------------------------------------------------------------
 
-- create()
function scene:create( event )
 
    local sceneGroup = self.view
    -- Code here runs when the scene is first created but has not yet appeared on screen
 
end
 
 
-- show()
function scene:show( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is still off screen (but is about to come on screen)
        local background = display.newRect(display.contentCenterX, display.contentCenterY, display.contentWidth, display.contentHeight)
        background:setFillColor( 1,0,1 )
        sceneGroup:insert( background )


        local title = display.newText("Menu Scene", display.contentWidth / 2, display.contentHeight / 2, native.systemFont, 48)
        title:setFillColor( 0,0,0 )
        sceneGroup:insert( title )


        local button = widget.newButton
        {
            label = "Go to Game",
            fontSize = 48,
            -- Properties for a rounded rectangle button
            shape = "roundedRect",
            width = 320,
            height = 100,
            cornerRadius = 2,
            fillColor = { default={1,1,1,1}, over={1,0.1,0.7,0.4} },
            strokeColor = { default={1,0.4,0,1}, over={0.8,0.8,1,1} },
            strokeWidth = 4,
            onEvent = function (event)
                if event.phase == "ended" then
                    composer.gotoScene("gameScene")
                end
            end
        }
        button.x = display.contentWidth / 2
        button.y = display.contentHeight / 2 - 100
        sceneGroup:insert(button)  
        
 
    elseif ( phase == "did" ) then
        -- Code here runs when the scene is entirely on screen
        

    end
end
 
 
-- hide()
function scene:hide( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is on screen (but is about to go off screen)
 
    elseif ( phase == "did" ) then
        -- Code here runs immediately after the scene goes entirely off screen
 
    end
end
 
 
-- destroy()
function scene:destroy( event )
 
    local sceneGroup = self.view
    -- Code here runs prior to the removal of scene's view
 
end
 
 
-- -----------------------------------------------------------------------------------
-- Scene event function listeners
-- -----------------------------------------------------------------------------------
scene:addEventListener( "create", scene )
scene:addEventListener( "show", scene )
scene:addEventListener( "hide", scene )
scene:addEventListener( "destroy", scene )
-- -----------------------------------------------------------------------------------
 
return scene
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

local composer = require( "composer" )
local physics = require( "physics" )
 
local scene = composer.newScene()
 
-- -----------------------------------------------------------------------------------
-- Code outside of the scene event functions below will only be executed ONCE unless
-- the scene is removed entirely (not recycled) via "composer.removeScene()"
-- -----------------------------------------------------------------------------------



-- -----------------------------------------------------------------------------------
-- Scene event functions
-- -----------------------------------------------------------------------------------
 
-- create()
function scene:create( event )
 
    local sceneGroup = self.view
    -- Code here runs when the scene is first created but has not yet appeared on screen
    -- start physics
    physics.start()
    physics.setGravity(0, 10)
    physics.setDrawMode("hybrid")

end
 
 
-- show()
function scene:show( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is still off screen (but is about to come on screen)
         local theGround1 = display.newImage( "./assets/sprites/land.png" )
            theGround1.x = 520
            theGround1.y = display.contentHeight
            theGround1.id = "the ground"
            physics.addBody( theGround1, "static", { 
            friction = 0.5, 
            bounce = 0.3 
            } )
        sceneGroup:insert( theGround1 )

        local theGround2 = display.newImage( "./assets/sprites/land.png" )
            theGround2.x = 1520
            theGround2.y = display.contentHeight
            theGround2.id = "the ground" -- notice I called this the same thing
            physics.addBody( theGround2, "static", { 
            friction = 0.5, 
            bounce = 0.3 
            } )
        sceneGroup:insert( theGround2 )

        local fallingSquare = display.newImage( "./assets/sprites/landSquare.png" )
            fallingSquare.x = display.contentWidth / 2
            fallingSquare.y = 0
            fallingSquare.id = "the falling block"
            physics.addBody( fallingSquare, "dynamic", { 
            friction = 0.5, 
            bounce = 0.3 
            } )
        sceneGroup:insert( fallingSquare )
 
    elseif ( phase == "did" ) then
        -- Code here runs when the scene is entirely on screen
        

    end
end
 
 
-- hide()
function scene:hide( event )
 
    local sceneGroup = self.view
    local phase = event.phase
 
    if ( phase == "will" ) then
        -- Code here runs when the scene is on screen (but is about to go off screen)
 
    elseif ( phase == "did" ) then
        -- Code here runs immediately after the scene goes entirely off screen
 
    end
end
 
 
-- destroy()
function scene:destroy( event )
 
    local sceneGroup = self.view
    -- Code here runs prior to the removal of scene's view
 
end
 
 
-- -----------------------------------------------------------------------------------
-- Scene event function listeners
-- -----------------------------------------------------------------------------------
scene:addEventListener( "create", scene )
scene:addEventListener( "show", scene )
scene:addEventListener( "hide", scene )
scene:addEventListener( "destroy", scene )
-- -----------------------------------------------------------------------------------
 
return scene
