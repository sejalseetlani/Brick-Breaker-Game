
package com.mycompany.game;
import java.awt.BasicStroke;

import java.awt.Color;

import java.awt.Graphics2D;

public class design {
    
    
        public int map[][];
    
    public int bkw;
    
    public int bkh;
    
    public design(int row, int col){
    
        map = new int[row][col];
        
        for(int i=0; i< map.length; i++){
            
            for(int j=0; j<map[0].length; j++){
                
                map[i][j]=1;
            }
        }
    
        bkw = 540/col;
        
        bkh= 150/row;
    }
    
    public void draw(Graphics2D g){
        
        for(int i=0; i< map.length; i++){
            
            for(int j=0; j<map[0].length; j++){
                
                if(map[i][j] > 0){
                    
                    g.setColor(Color.gray);
                    
                    g.fillRect(j*bkw + 80, i*bkh+50, bkw, bkh);
                    
                    g.setStroke(new BasicStroke(3));
                    
                    g.setColor(Color.cyan);
                    
                    g.drawRect(j*bkw + 80, i*bkh+50, bkw, bkh);
                }
            }
            
        }
    
    }
    
    public void setBrickValue(int value, int row , int col){
     
        map[row][col] = value;   
     
    }
        
        
    
}

