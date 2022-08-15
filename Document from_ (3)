/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.game;


import java.awt.Color;

import java.awt.Font;

import java.awt.Graphics;

import java.awt.Graphics2D;

import java.awt.Rectangle;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.event.KeyEvent;

import java.awt.event.KeyListener;

import javax.swing.JPanel;

import javax.swing.Timer;
public class play extends JPanel implements KeyListener , ActionListener{ 
    boolean plays = false;
    
    int score = 0;
    
    int totalbricks = 21;
    
    Timer time;
    
    int delay = 8;
    
    int px = 310;
    
    int bpx = 120;
    
    int bpy = 350;
    
    int bdx = -1;
    
    int bdy = -2;
    
    design map;
    
    public play(){
        
        map = new design(3,7);
        
        addKeyListener(this);
        
        setFocusable(true);
        
        setFocusTraversalKeysEnabled(false);
        
        time = new Timer(delay,this);
        
        time.start();
        
    }
    
    public void paint(Graphics g){
        
        //background
        
        g.setColor(Color.cyan);
        
        g.fillRect(1, 1, 692, 592);
        g.fillRect(px, px, WIDTH, HEIGHT);

        // map 
        
        map.draw((Graphics2D)g);
        
        
        //border
        
        g.setColor(Color.black);
        
        g.fillRect(0, 0, 3, 592);
        
        g.fillRect(0, 0, 69, 3);
        
        g.fillRect(691, 0, 3, 592);
        
        
        //score
        
        g.setColor(Color.black);
        
        g.setFont(new Font("serif",Font.BOLD, 25));
        
        g.drawString(""+score, 590, 30);
        
        
        //paddle
        
        g.setColor(Color.MAGENTA);
        
        g.fillRect(px, 550, 100, 8);
        
        
        //ball
        
        g.setColor(Color.red);
        
        g.fillOval(bpx, bpy, 20, 20);
        
        if(totalbricks<=0){
        
            plays = false;
            
            bdx=0;
            
            bdy=0;
            
            g.setColor(Color.red);
            
            g.setFont(new Font("serif",Font.BOLD, 30));
            
            g.drawString("You won", 260, 300);
            
            
            g.setFont(new Font("serif",Font.BOLD, 20));
            
            g.drawString("Press Enter to Restart", 230, 350);
        
        }
        
        if(bpy>570){
            
            plays = false;
            
            bdx=0;
            
            bdy=0;
            
            g.setColor(Color.red);
            
            g.setFont(new Font("serif",Font.BOLD, 30));
            
            g.drawString("Game Over, Score: "+score, 190, 300);
            
            
            
            g.setFont(new Font("serif",Font.BOLD, 20));
            
            g.drawString("Press Enter to Restart", 230, 350);
        
        }
        
        
        g.dispose();
    }
    
    
    
    @Override
    public void keyPressed(KeyEvent e) {
        
        if(e.getKeyCode()== KeyEvent.VK_RIGHT){
         
            if(px>=600){
             
                px = 600;
         }   
         else{
             
                moveRight();
         }
        
        }
        
        
        if(e.getKeyCode()== KeyEvent.VK_LEFT){
            
            if(px < 10){
             
                px = 10;
            
            }   
         else{
             
                moveLeft();

            }
        
        }
        
        
        if(e.getKeyCode()== KeyEvent.VK_ENTER){
            
            if(!plays){
                
                plays = true;
                
                bpx = 120;
                
                bpy=350;
                
                bdx=-1;
                
                bdy=-2;
                
                px=310;
                
                score =0;
                
                totalbricks=21;
                
                map=new design(3,7);
                
            
            }
        
        }
    
    }
    

    public void moveRight(){
        
        plays = true;
        
        px += 20;
    
    }
    
    public void moveLeft(){
        
        plays = true;
        
        px -= 20;
    
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        
        time.start();
        
        if(plays){
            
            if(new Rectangle(bpx , bpy, 20 ,20).intersects(new Rectangle(px,550,100,8))){
            
                bdy= -bdy;
        
            }
            for(int i=0; i<map.map.length; i++){
                
                A: for(int j=0; j<map.map[0].length; j++){
                    
                    if(map.map[i][j] > 0){
                        
                        int bkx = j*map.bkw+80;
                        
                        int bky = i*map.bkh+50;
                        
                        int bkw = map.bkw;
                        
                        int bkh = map.bkh;
                        
                        
                        Rectangle rect = new Rectangle(bkx,bky,bkw,bkh);
                        
                        Rectangle ballrect = new Rectangle(bpx,bpy,20,20);
                        
                        Rectangle brickrect= rect;
                        
                       
                        
                        if(ballrect.intersects(brickrect)){
                            
                            map.setBrickValue(0, i, j);
                            
                            totalbricks--;
                            
                            score+=5;
                            
                            if(bpx+19 <=brickrect.x || bpx + 1 >= brickrect.x + brickrect.width){
                                
                                bdx = -bdx;
                            
                            
                            }else{
                                
                                bdy = -bdy;
                            }
                            break A;
                        
                        }
                    
                    }
                
                }
            
            }
            
            bpx += bdx;
            
            bpy +=bdy;
            
            if(bpy < 0){
               
                bdy = -bdy;
           
            }
           
            if(bpx > 670){
               
                bdx = -bdx;
           
            }
           
            
            if(bpx < 0){
               
                bdx = -bdx;
           
            }
        
        }
        
        repaint();
    
    }
    @Override
    public void keyTyped(KeyEvent e){}
    
    @Override
    public void keyReleased(KeyEvent e) {}
}
