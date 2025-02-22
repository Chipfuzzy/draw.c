import pygame,sys
from pygame.locals import QUIT

pygame.init()
screen = pygame.display.set_mode((500,500))
pygame.display.set_caption("draw")
back = (0,0,0)
white = (255,255,255)
red = (0,0,255)
blue = (0,255,0)
green = (255,0,0)
screen.fill("white")
pygame.display.update()
while True:
    class myCircle:
        def __init__(self,color,pos,rad, wid=0):
            self.Circle_surf = screen
            self.Circle_color = color
            self.Circle_pos = pos
            self.Circle_rad = rad
            self.wid = wid
            self.scrn = screen

        def draw(self):
            pygame.draw.circle(self.scrn, self.color, self.pos, self.rad, self.wid )

        def grow(self,x):
            self.rad += x
            pygame.draw.circle(self.scrn, self.color, self.pos, self.rad, self.wid )
    
    greenCircle=Circle(green,(400,400),50)
    redCircle=Circle(red,(100,300),30)
    blueCircle=Circle(blue,(300,200),50)

    
    greenCircle.draw()
    redCircle.draw()
    blueCircle.draw()

    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            sys.exit()
    pygame.display.update()
