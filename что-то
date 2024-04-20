from pygame import *
from random import randint
from time import time as timer
#создай окно игры
win_width = 700
win_height = 500
window = display.set_mode((700, 500))
display.set_caption('Шутер')
bk = transform.scale(image.load('galaxy.jpg'), (700, 500))
mixer.init()
mixer.music.load('space.ogg')
mixer.music.play()

lost = 0
point = 0
font.init()
font1 = font.SysFont('Arial', 36)
font2 = font.SysFont('Arial', 70)
font3 = font.SysFont('Arial', 70)
win = font3.render('YOU WIN', True, (255, 215, 0))
folse = font2.render('YOU LOSE', True, (255, 0, 0))
text_shd = font1.render('Счёт:'+ str(point),1,(255, 160, 122))
text_lose = font1.render('Пропущено:' + str(lost),1,(255, 160, 122))

num_fire = 0
rel_time = False





run = True
FPS = 60
clock = time.Clock()
finish = False
class GameSprite(sprite.Sprite):
    def __init__ (self, player_image, player_x, player_y, player_speed):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (65,65))
        self.speed = player_speed
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y
    def reset(self):
        window.blit(self.image,(self.rect.x, self.rect.y))

class Player(GameSprite):
    def update(self):
        keys_pressed = key.get_pressed()
        if keys_pressed[K_a] and self.rect.x > 5:
            self.rect.x -= self.speed
        if keys_pressed[K_d] and self.rect.x < win_width - 80:
            self.rect.x += self.speed
       
        #if keys_pressed[K_s] and self.rect.y < win_height - 80:
        #    self.rect.y += self.speed
    def fire(self):
        bullet = Bullet('bullet.png', self.rect.centerx, self.rect.top, 5)
        bullets.add(bullet)
        mixer.music.load('fire.ogg')
        mixer.music.load('space.ogg')
        mixer.music.play()
        #global point
        #global lost
        #if point += 1:
            #mixer.music.load('space.ogg')
            #mixer.music.play()
        #if lost += 1:
            #mixer.music.load('space.ogg')
            #mixer.music.play()
            
#-40 начало
class Enemy(GameSprite):
    def update(self):
        self.rect.y += self.speed
        global lost
        if self.rect.y > 550:
            self.rect.y = -40
            self.rect.x = randint(0, 650)
            
            lost += 1



class Asteroid(GameSprite):
    def update(self):
        #asteroid1 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
        self.rect.y += self.speed
        self.rect.x += self.speed
        if self.rect.y > 400:
            self.kill()
        if self.rect.x > 650:
            self.kill()
        if self.rect.x > 0:
            self.kill()
        if self.rect.y > 0:
            self.kill()
        if self.rect.y > 400:
            self.kill()


            

asteroid2 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroid3 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroid4 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroid5 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroid6 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroid7 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)








class Bullet(GameSprite):
    def update(self):
        self.rect.y -= self.speed
        if self.rect.y < 0:
            self.kill()




asteroids = sprite.Group()
asteroid1 = Asteroid(player_image = "asteroid.png", player_x = randint(0, 650), player_y = randint(0, 500), player_speed= 1)
asteroids.add(asteroid1)


bullets = sprite.Group()

monsters = sprite.Group()
for i in range(5):
    monster = Enemy(player_image = 'ufo.png', player_x = randint(0,650), player_y = -40, player_speed = 5)
    monsters.add(monster)
player = Player(player_image = 'rocket.png', player_x = 100, player_y = 400, player_speed = 12)





while run:
    for e in event.get():
        if e.type == QUIT:
            run = False
        if e.type == KEYDOWN:
            if e.key  == K_SPACE:
                if num_fire < 5 and rel_time == False:
                    num_fire = num_fire + 1
                    player.fire()

                if num_fire >= 5 and rel_time == False:
                    last_time = timer()
                    rel_time = True
        


                    
    if finish != True:   
        window.blit(bk,(0,0))
        window.blit(text_lose,(50,50))
        monsters.draw(window)
        bullets.draw(window)
        window.blit(text_shd,(50,100))
        bullets.update()
        monsters.update()
        player.update()
        player.reset()
        #asteroid1.update()
        #asteroid1.reset()
        if point == 1:
            asteroid1.reset()
            asteroid1.update()
        
        if point == 4:
            asteroid2.reset()
            asteroid2.update()
        if point == 6:
            asteroid3.reset()
            asteroid3.update()
        if point == 8:
            asteroid4.reset()
            asteroid4.update()
        if point == 9:
            asteroid5.reset()
            asteroid5.update()
        if point == 10:
            asteroid6.reset()
            asteroid6.update()
        if point == 11:
            asteroid7.reset()
            asteroid7.update()
        if rel_time == True:
            now_time = timer()

            if now_time - last_time < 3:
                reload = font2.render('wait,reload...',1,(150,0,0))
                window.blit(reload,(260,460))
            else:
                num_fire = 0
                rel_time = False
        
        
        
    text_shd = font1.render('Счёт:'+ str(point),1,(255, 160, 122))
    text_lose = font1.render('Пропущено:' + str(lost),1,(255, 160, 122))
    
    #if point == 9:




    if lost >= 20 or sprite.spritecollide(player, monsters, True):#or sprite.spritecollide(player, asteroid, True)#
        window.blit(folse,(200, 350))
        finish = True
    if point >= 13:
        window.blit(win,(250, 200))
        finish = True
    
    sprites_list = sprite.groupcollide(monsters, bullets, True, True)
    for i in sprites_list:
        point += 1
        for i in range(1):
            monster = Enemy(player_image = 'ufo.png', player_x = randint(0,650), player_y = -40, player_speed = 5)
            monsters.add(monster)
    #if sprite.spritecollide(player, asteroids, True):
        #asteroid1.kill()
        #point -= 1





    display.update()
    clock.tick(FPS)

