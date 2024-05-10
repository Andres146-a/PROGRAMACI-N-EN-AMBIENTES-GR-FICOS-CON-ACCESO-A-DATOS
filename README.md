# PROGRAMACI-N-EN-AMBIENTES-GR-FICOS-CON-ACCESO-A-DATOS
DEBERES-TALLER-PROYECTOS
Estudiante: Matias Andres Cañola Salazar

Descripción del deber:
Para este deber se nos solicitó usar layouts. 
Para eso: 
1. Se importan las clases necesarias de las bibliotecas estándar de Java.
2. Se define la clase VentanaPrincipal, que contiene el método principal main y otros métodos para inicializar y configurar la interfaz de usuario.
3. La interfaz de usuario consta de un JFrame principal que contiene varios componentes, incluidos paneles, etiquetas, campos de texto, botones, separadores y una lista desplegable.
4. Se establecen disposiciones y configuraciones de estilo para los componentes, como colores de fondo, fuentes y dimensiones.
5. Se aplican acciones a algunos componentes, como la capacidad de arrastrar y soltar una etiqueta.
6. Se añaden escuchadores de eventos para manejar las interacciones del usuario, como hacer clic en botones o cambiar el tamaño de la ventana.

**METODOS UTILIZADOS**:

	**1. Textfield**
	Se creo un text fiel en el diseño del proyecto , en este código crea un TextField, establece su posición vertical (top) y horizontal (left) dentro del AnchorPane, y luego lo agrega al AnchorPane para que sea visible en la interfaz de usuario..

	**2. ListView**
	Aqui se crea un ListView y se agrega al AnchorPane. Aquí está el fragmento relevante: Este código crea un ListView vacío y establece su posición dentro del AnchorPane. En este caso, se posiciona en la parte superior izquierda (20.0 desde la parte superior y 220.0 desde la izquierda). Luego, el ListView se agrega al AnchorPane para que sea visible en la interfaz de usuario.

	**3. Metodo label**
	En el método agregarLabels, se llaman varias veces al método agregarLabel para agregar etiquetas al AnchorPane. Cada llamada especifica el texto y la posición de una etiqueta diferente.

	**4. Agregar el label**
	El método agregarLabel crea un objeto Label con el texto proporcionado y luego establece la posición superior e izquierda del Label en el AnchorPane utilizando los métodos estáticos setTopAnchor y setLeftAnchor de la clase AnchorPane. Finalmente, agrega el Label al AnchorPane llamando al método getChildren().add(label) del AnchorPane.

EJECUCIÓN

![image](https://github.com/Andres146-a/PROGRAMACI-N-EN-AMBIENTES-GR-FICOS-CON-ACCESO-A-DATOS/assets/124753237/294c10db-041a-4aa2-8da2-5eb1d10cec73)
![Deber ambiente](https://github.com/Andres146-a/PROGRAMACI-N-EN-AMBIENTES-GR-FICOS-CON-ACCESO-A-DATOS/assets/124753237/d0c02bb7-e3a9-4231-9f40-bf3ce142d9b8)

CÓDIGO:

package pruebaGrafica2;import java.awt.EventQueue;
import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.Image;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;

import javax.swing.ImageIcon;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JList;
import javax.swing.JTextField;
import javax.swing.SwingConstants;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JSeparator;
import java.awt.List;
import java.awt.Window;

import javax.swing.JButton;
import javax.swing.UIManager;

public class VentanaPrincipal {

    private JFrame frame;
    private JTextField textField;
    private JPanel panel;
    private JLabel label1;
    private JLabel label2;
    private JLabel label3;
    private JLabel label4;
    private JLabel draggablePiece;

    private int lastY;

    public static void main(String[] args) {
        EventQueue.invokeLater(new Runnable() {
            public void run() {
                try {
                    VentanaPrincipal window = new VentanaPrincipal();
                    window.frame.setVisible(true);
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        });
    }

    public VentanaPrincipal() {
        initialize();
    }

    private void initialize() {
        frame = new JFrame();
        frame.setBounds(100, 100, 712, 572);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Panel principal con BorderLayout
        panel = new JPanel(new BorderLayout());
        frame.getContentPane().add(panel);

        // Panel para los componentes del centro
        JPanel centerPanel = new JPanel(null);
        centerPanel.setBorder(UIManager.getBorder("Button.border"));
        centerPanel.setBackground(new Color(240, 240, 240));
        panel.add(centerPanel, BorderLayout.CENTER);

        // Imágenes para los labels
        ImageIcon image1 = new ImageIcon("C:\\Users\\Matias\\OneDrive\\UNIVERSIDAD\\3SEMESTRE\\Programación en ambiente grafico\\Curso_Java\\pruebaGrafica2\\src\\imagenes\\OIG4 (2).jpeg");
        ImageIcon image2 = new ImageIcon("C:\\Users\\Matias\\OneDrive\\UNIVERSIDAD\\3SEMESTRE\\Programación en ambiente grafico\\Curso_Java\\pruebaGrafica2\\src\\imagenes\\OIG4 (3).jpeg"); // Cambia la ruta de la imagen 2
        ImageIcon image3 = new ImageIcon("C:\\Users\\Matias\\OneDrive\\UNIVERSIDAD\\3SEMESTRE\\Programación en ambiente grafico\\Curso_Java\\pruebaGrafica2\\src\\imagenes\\OIG4 (4).jpeg"); // Cambia la ruta de la imagen 3
        ImageIcon image4 = new ImageIcon("C:\\Users\\Matias\\OneDrive\\UNIVERSIDAD\\3SEMESTRE\\Programación en ambiente grafico\\Curso_Java\\pruebaGrafica2\\src\\imagenes\\OIG4.jpeg"); // Cambia la ruta de la imagen 4

        // Escalamos las imágenes a 100x100 píxeles
        Image scaledImage1 = image1.getImage().getScaledInstance(100, 100, Image.SCALE_SMOOTH);
        Image scaledImage2 = image2.getImage().getScaledInstance(100, 100, Image.SCALE_SMOOTH);
        Image scaledImage3 = image3.getImage().getScaledInstance(100, 100, Image.SCALE_SMOOTH);
        Image scaledImage4 = image4.getImage().getScaledInstance(100, 100, Image.SCALE_SMOOTH);

        // Creamos los JLabels con las imágenes y los agregamos al panel
        JLabel imagenLabel1 = new JLabel(new ImageIcon(scaledImage1));
        imagenLabel1.setBounds(60, 31, 100, 100); // Modifica las dimensiones de la imagen
        centerPanel.add(imagenLabel1);

        JLabel imagenLabel2 = new JLabel(new ImageIcon(scaledImage2));
        imagenLabel2.setBackground(new Color(128, 64, 64));
        imagenLabel2.setBounds(60, 142, 100, 100); // Modifica las dimensiones de la imagen
        centerPanel.add(imagenLabel2);

        JLabel imagenLabel3 = new JLabel(new ImageIcon(scaledImage3));
        imagenLabel3.setBounds(60, 258, 100, 100); // Modifica las dimensiones de la imagen
        centerPanel.add(imagenLabel3);

        JLabel imagenLabel4 = new JLabel(new ImageIcon(scaledImage4));
        imagenLabel4.setBounds(60, 380, 100, 100); // Ajusta la posición vertical de la imagen del label 4
        centerPanel.add(imagenLabel4);

        // Textos para los labels
        label1 = new JLabel("Nombre y Apellido");
        label1.setForeground(new Color(128, 64, 64));
        label1.setBackground(new Color(128, 64, 0));
        label1.setHorizontalAlignment(SwingConstants.LEFT);
        label1.setBounds(170, 54, 129, 48);
        centerPanel.add(label1);

        label2 = new JLabel("Nombre y Apellido");
        label2.setForeground(new Color(128, 64, 64));
        label2.setBackground(new Color(240, 240, 240));
        label2.setHorizontalAlignment(SwingConstants.LEFT);
        label2.setBounds(170, 160, 129, 48);
        centerPanel.add(label2);

        label3 = new JLabel("Nombre y Apellido");
        label3.setForeground(new Color(128, 64, 64));
        label3.setHorizontalAlignment(SwingConstants.LEFT);
        label3.setBounds(170, 255, 129, 48);
        centerPanel.add(label3);

        label4 = new JLabel("Nombre y Apellido");
        label4.setForeground(new Color(128, 64, 64));
        label4.setHorizontalAlignment(SwingConstants.LEFT);
        label4.setBounds(170, 364, 129, 48);
        centerPanel.add(label4);

        // Campo de texto
        textField = new JTextField();
        textField.setBounds(390, 400, 296, 30); // Se ajusta la posición del TextField
        centerPanel.add(textField);

        // Barra de progreso
        draggablePiece = new JLabel();
        draggablePiece.setBackground(new Color(128, 128, 128));
        draggablePiece.setOpaque(true);
        draggablePiece.setBounds(10, 31, 18, 30); 
        draggablePiece.addMouseListener(new MouseAdapter() {
            @Override
            public void mousePressed(MouseEvent e) {
                lastY = e.getY();
            }
        });
        draggablePiece.addMouseMotionListener(new MouseAdapter() {
            @Override
            public void mouseDragged(MouseEvent e) {
                int deltaY = e.getY() - lastY;
                int newY = draggablePiece.getY() + deltaY;
                
                // Se limita el movimiento para que no se salga de los límites de la ventana
                if (newY >= 31 && newY <= centerPanel.getHeight() - 70 - 27) {
                    draggablePiece.setLocation(draggablePiece.getX(), newY);
                }
            }
        });
        centerPanel.add(draggablePiece);

        // Separador
        JSeparator separator = new JSeparator();
        separator.setForeground(Color.BLACK);
        separator.setBackground(Color.BLACK);
        separator.setBounds(230, 31, 0, 328);
        centerPanel.add(separator);
        
        // Lista de ejemplo
        String[] data = {"Elemento 1", "Elemento 2", "Elemento 3", "Elemento 4", "Elemento 5"};
        JList<String> list = new JList<>(data);
        
     // Creamos un JScrollPane y configuramos su apariencia
        JScrollPane scrollPane = new JScrollPane(list);
        scrollPane.getVerticalScrollBar().setPreferredSize(new Dimension(0, 0)); // Quita el grosor de la barra vertical
        scrollPane.getVerticalScrollBar().setBackground(Color.LIGHT_GRAY); // Cambia el color de la barra vertical
        scrollPane.getHorizontalScrollBar().setPreferredSize(new Dimension(0, 0)); // Quita el grosor de la barra horizontal
        scrollPane.getHorizontalScrollBar().setBackground(Color.LIGHT_GRAY); // Cambia el color de la barra horizontal
        scrollPane.setBounds(390, 50, 296, 327); // Se ajusta la posición y se da espacio entre el JTextField y la lista
        centerPanel.add(scrollPane);
        
        JButton btnNewButton = new JButton("Agregar");
        btnNewButton.setBounds(170, 95, 89, 23);
        centerPanel.add(btnNewButton);
        
        JButton btnNewButton_1 = new JButton("Agregar");
        btnNewButton_1.setBounds(170, 206, 89, 23);
        centerPanel.add(btnNewButton_1);
        
        JButton btnNewButton_2 = new JButton("Agregar");
        btnNewButton_2.setBounds(170, 314, 89, 23);
        centerPanel.add(btnNewButton_2);
        
        JButton btnNewButton_3 = new JButton("Agregar");
        btnNewButton_3.setBounds(170, 423, 89, 23);
        centerPanel.add(btnNewButton_3);

        
        frame.addComponentListener(new java.awt.event.ComponentAdapter() {
            private Window scrollPane1;

			public void componentResized(java.awt.event.ComponentEvent evt) {
                // Ajuste de el tamaño del JTextField
                textField.setSize(centerPanel.getWidth() - 410, 30); // Se ajusta el tamaño del TextField

                // Ajuste de la posición vertical del JTextField
                int textFieldY = centerPanel.getHeight() - 70 - 27;

                // Nos aseguramos de que la posición no sea negativa
                if (textFieldY < 31) {
                    textFieldY = 31;
                }

                // Ajuste de  la posición del JTextField
                textField.setLocation(390, textFieldY); // Se ajusta la posición del TextField
                
                // Ajuste de el tamaño y la posición del JScrollPane
                scrollPane1.setBounds(390, 90, centerPanel.getWidth() - 410, centerPanel.getHeight() - 70 - 127); // Se ajusta la posición y el tamaño de acuerdo al espacio
            }
        });
    }
}

