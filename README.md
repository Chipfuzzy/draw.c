import pygame,sys
from pygame.locals import QUIT

pygame.init()
screen = pygame.display.set_mode((500,500))
pygame.display.set_caption("draw")
black = (0,0,0)
white = (255,255,255)
red = (0,0,255)
blue = (0,255,0)
green = (255,0,0)
yellow = (255,255,0)
screen.fill("white")
pygame.display.update()

class myCircle:
    def __init__(self,color,pos,rad, wid=0):
        self.Circle_surf = screen
        self.color = color
        self.pos = pos
        self.rad = rad
        self.wid = wid
        self.scrn = screen

    def draw(self):
        pygame.draw.circle(self.scrn, self.color, self.pos, self.rad, self.wid )

    def grow(self,x):
        self.rad += x
        pygame.draw.circle(self.scrn, self.color, self.pos, self.rad, self.wid )
    
position = (300,300)
radius = 50
wid = 2
pygame.draw.circle(screen, red, position, radius, wid)
pygame.display.update()

blueCircle = myCircle(blue, position, radius+60)
redCircle = myCircle(red, position, radius+40)
yellowCircle = myCircle(yellow, position, radius, 5)
greenCircle = myCircle(green, position, radius, 20)

while(1):
    for event in pygame.event.get():
        if (event.type == pygame.MOUSEBUTTONDOWN):
            blueCircle.draw()
            redCircle.draw()
            yellowCircle.draw()
            greenCircle.draw()
            pygame.display.update()
        elif (event.type == pygame.MOUSEBUTTONUP):
            blueCircle.grow(2)
            redCircle.grow(2)
            yellowCircle.grow(2)
            greenCircle.grow(2)
            pygame.display.update()
        elif (event.type == pygame.MOUSEMOTION):
            pos = pygame.mouse.get_pos()
            blackCircle = myCircle(black, pos, 5)
            blackCircle.draw()
            pygame.display.update()

        elif event.type == QUIT:
            pygame.quit()
            sys.exit()
    pygame.display.update()
