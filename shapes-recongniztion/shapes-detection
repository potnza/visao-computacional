import cv2
import matplotlib.pyplot as plt
import numpy as np


def preprocess_image(image_path):
    # Carrega a imagem em escala de cinza
    image = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
    
    # Aplica um limiar binário para criar uma imagem binária
    _, thresh = cv2.threshold(image, 128, 255, cv2.THRESH_BINARY)
    return thresh

def detect_shapes(thresh_image):
    # Encontra contornos na imagem binária
    contours, _ = cv2.findContours(thresh_image, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    
    # Cria uma cópia da imagem original para desenhar os contornos
    shape_image = cv2.cvtColor(thresh_image, cv2.COLOR_GRAY2BGR)
    
    for contour in contours:
        # Aproxima o contorno para uma forma poligonal
        epsilon = 0.02 * cv2.arcLength(contour, True)
        approx = cv2.approxPolyDP(contour, epsilon, True)
        
        # Desenha o contorno na imagem
        cv2.drawContours(shape_image, [approx], 0, (0, 255, 0), 3)
        
        # Identifica a forma
        x, y, w, h = cv2.boundingRect(approx)
        if len(approx) == 3:
            shape = 'Triangulo'
        elif len(approx) == 4:
            aspect_ratio = float(w) / h
            shape = 'Quadrado' if 0.95 <= aspect_ratio <= 1.05 else 'Retangulo'
        elif len(approx) > 4:
            shape = 'Circulo'
        else:
            shape = 'Desconhecido'
        
        # Adiciona texto na imagem
        cv2.putText(shape_image, shape, (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.9, (255, 0, 0), 2)

    return shape_image

def main(image_path):
    # Processamento da imagem.
    thresh_image = preprocess_image(image_path)
    shape_image = detect_shapes(thresh_image)
    
    # Converte de BGR para RGB para exibir com Matplotlib
    shape_image_rgb = cv2.cvtColor(shape_image, cv2.COLOR_BGR2RGB)
    plt.imshow(shape_image_rgb)
    plt.title('Detected Shapes')
    plt.axis('off')  # Não exibir eixos
    plt.show()

if __name__ == "__main__":
    main('shapes.jpg')  # Pode substituir por uma imagem que deseja testar
