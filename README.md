import pygame
import time
import random 
pygame.init()

size=[700,500] #СЂР°Р·РјРµСЂ РѕРєРЅР°
screen=pygame.display.set_mode(size) #РѕС‚РєСЂС‹РІР°СЋС‰РёРµСЃСЏ РѕРєРЅРѕ
pygame.display.set_caption("РџСЂРѕРµРєС‚")

black=( 0, 0, 0)
white=( 255, 255, 255)
green=( 0, 255, 0)
red=( 255, 0, 0)

pygame.image.load("2666412454397924020.jpg")


player_image = pygame.image.load("wpacCSflPhM.jpg").convert()
player_image.set_colorkey(white)

background_position = [0,0]
background_image=pygame.image.load("2666412454397924020.jpg").convert()
token_image = pygame.image.load("token.jpg").convert()
token_image.set_colorkey(white) 
x=0
y=0
n=0
x_speed=0
y_speed=0
px_speed=0
py=30
ty=py
tx=30
tx_speed=0
mx=0
time=100
my=0
tx_speed=0

score=0

##def ataka(ty,tx):
##    global mx,my,monster_image,score,token_image
##    while tx<700:
##          tx=tx+5
##          print (tx)
##          if (mx<=tx+20<=mx+110) and (my<=ty+20<=my+110):
##            score=score+1
##            print (score)
##            monster_image=0
##            done= True
        
def monstr():
  monster_image=pygame.image.load("monstr.jpg").convert()
  monster_image.set_colorkey(white)
  mx=random.randint(200,590)
  my=random.randint (0,500)
  screen.blit (monster_image,[mx,my])  
  
 
done = False
timer = pygame.time.Clock()
clock=int(pygame.time.get_ticks()/1000)

while not done:
  
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            done = True
            
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
               x_speed=-1
            if event.key == pygame.K_RIGHT:
                x_speed=1
            if event.key == pygame.K_UP:
                y_speed=-1
            if event.key == pygame.K_DOWN:
                y_speed=1
            if event.key == pygame.K_1:
                py=30
            if event.key == pygame.K_2:
                py=140
            if event.key == pygame.K_3:
                py=250
            if event.key == pygame.K_4:
                py=360
            if event.key == pygame.K_SPACE:
                player_image=pygame.image.load("wpacCSflPhM2.jpg").convert()
                player_image.set_colorkey(white)
                tx_speed=28
                screen.blit(player_image,[0,py])
                
##                ataka(py,30)

                
                                
                
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_LEFT: 
                x_speed=0
            if event.key == pygame.K_RIGHT:
                x_speed=0
            if event.key == pygame.K_UP:
                y_speed=0
            if event.key == pygame.K_DOWN:
                y_speed=0
            if event.key == pygame.K_SPACE:
                player_image=pygame.image.load("wpacCSflPhM.jpg").convert()
                player_image.set_colorkey(white)
                
                    
                
    screen.blit(background_image, background_position)

    if (mx==tx) and (my==py):
            score=score+1
            print (score)
            monster_image=0
            done= True
        
    x=x+x_speed
    y=y+y_speed
    tx=tx+tx_speed

   

    if clock%15==0:
      monstr()

    if tx>700:
        tx=0
        tx_speed=0
        n=n+1

    if n==6:
        done=True

    screen.blit(token_image, [tx,py+60])    
    screen.blit(player_image, [0,py])
    
    pygame.draw.ellipse(screen,black,[x,y,30,30],6)
    
    pygame.display.flip()
 
    timer.tick(5)
 

pygame.quit()
