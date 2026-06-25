# pproyecto-pensamiento-computacional-S5

codigo casi final con las imagenes trabajadas en illustraitor. 

 Primera parte: la estrella trsite, con la nube representando sus pensamientos y tintineando, para llamar la atencion del espectador y aue hagan click dentro de ella. 

let estrella;
let nube;
let contorno;

function preload() {
  estrella = loadImage("estrella1.png");
  nube = loadImage("nube1.png");
  contorno = loadImage("contornonube.png");
}

function setup() {
  createCanvas(900, 900);
}

function draw() {
  background(255);

  // Estrella triste
  image(estrella, 0, 0, width, height);

  // Efecto de tintineo
  let alpha = 180 + 75 * sin(frameCount * 0.1);

  tint(255, alpha);
  image(nube, 0, 0, width, height);
  image(contorno, 0, 0, width, height);
  noTint();
} 

Segunda parte: hacen click dentro de la nube esta se agrandara para mostrar el por que de la tristeza se la estrellita. (gracias santi por el codigo) 

Segunda parte 
let escena = 1;

let tamanoNube = 300;
let agrandamiento = false;

function mousePressed(){

  if(escena == 1){
    escena = 2;
    agrandamiento = true;
  }

}

Y debajo de draw va 

if(escena == 2){

  if(agrandamiento == true){
    tamanoNube = tamanoNube + 4;
  }

  image(nube,
        width/2 - tamanoNube/2,
        height/2 - tamanoNube/2,
        tamanoNube,
        tamanoNube);
}

tercra parte(en el codigo esta mezclada con la cuarta parte): Aca se muesyra a la estrellita con otra estrella que era su pareja, en medio hay un vorazon que tambien esta titineando, este al apretarlo se rompe y en eso se salen de la estrella y se vuelve a la imagen inicial. 

Parte tres /cuatro
escena = 4;
lagrimaY = 0;


Function draw 
if(escena == 4){

  // Fondo
  image(estrellaLlorando, 0, 0, width, height);

  // Nube de pensamiento
  image(nube, 0, 0, width, height);

  // Lágrima cayendo
  image(lagrima, 350, 420 + lagrimaY, 20, 30);

  lagrimaY = lagrimaY + 3;

  // Cuando llega abajo, vuelve arriba
  if(lagrimaY > 70){
    lagrimaY = 0;
  }

}

function mousePressed(){

  if(escena == 3){

    if(mouseX > 420 && mouseX < 500 &&
       mouseY > 380 && mouseY < 470){

      escena = 4;

    }

  }

}

Cuarta parte oficial: aca la estrella esta llorando, el let esta en el codigo anetrior, yyy cuando la la persona mueva el mouse aparecera atras un verso de la cancion, que es "quererte hasta que duela" y desaparezera moviendo el mouse. 

Parte cuatro oficial 

let mostrarTexto = false;
let tiempoMovimiento = 0;

Función del mouse 
function mouseMoved() {
  mostrarTexto = true;
  tiempoMovimiento = frameCount;
}

Abajo en el draw 

if (escena == 5) {

  // Estrella
  image(estrellaLlorando, 0, 0, width, height);

  // Si el mouse dejó de moverse, vuelve la nube
  if (frameCount - tiempoMovimiento > 20) {
    mostrarTexto = false;
  }

  if (mostrarTexto) {

    fill(135, 206, 250); // Celeste
    textStyle(BOLD);
    textAlign(CENTER, CENTER);
    textSize(40);

    text("QUERERTE\nHASTA QUE DUELA", width/2, height/2);

  } else {

    image(nube, 0, 0, width, height);

  }
}

quienta parte: como dijimos anteiormente, desparece todo moviendo el mouse, junto a las letras desaparece igual la nube y aparece un parche curita y un corazon roto en la estrella. 

Parte cinco 

function mouseReleased() {

  arrastrando = false;

  // Zona del corazón
  if (curitaX > 420 &&
      curitaX < 480 &&
      curitaY > 450 &&
      curitaY < 510) {

    curitaPegada = true;
  }

}

Abajo en draw 

// Corazón roto
image(corazonRoto, 430, 460, 60, 60);

// Si ya está pegada la curita
if (curitaPegada) {
  image(curita, 425, 455, 70, 70);
}

Y para q la curita siga titineando 
let brillo = 180 + 75 * sin(frameCount * 0.1);

tint(255, brillo);
image(curita, curitaX, curitaY, 100, 70);
noTint();

ultima parte(al fin ): aca la toman el parche curita con el mouse loc colofan en el corazon roto y la estrela cambia de color y esta un poco mas feliz, ya que se curo (jaja) entonves detras de la estrella vuelve a aparecer un verso de la canciom pero esta vez es " soy de amor sin amor" 
