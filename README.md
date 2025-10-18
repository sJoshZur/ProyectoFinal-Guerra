# 📝 Código Completo - Quiz Bolivia en GameMaker Studio 2

## Script 1: scr_init_questions
Inicializa todas las preguntas del juego

```gml
function init_questions() {
    questions = ds_list_create();
    
    // Pregunta 1
    var q1 = ds_map_create();
    q1[? "pregunta"] = "¿En qué año se proclamó la independencia de Bolivia?";
    q1[? "opcion1"] = "1821";
    q1[? "opcion2"] = "1825";
    q1[? "opcion3"] = "1830";
    q1[? "opcion4"] = "1842";
    q1[? "respuesta"] = 2;  // Opción 2 es correcta (1825)
    ds_list_add(questions, q1);
    
    // Pregunta 2
    var q2 = ds_map_create();
    q2[? "pregunta"] = "¿Quién fue el primer presidente de Bolivia?";
    q2[? "opcion1"] = "Simón Bolívar";
    q2[? "opcion2"] = "Antonio José de Sucre";
    q2[? "opcion3"] = "José Ballivián";
    q2[? "opcion4"] = "Andrés de Santa Cruz";
    q2[? "respuesta"] = 2;
    ds_list_add(questions, q2);
    
    // Pregunta 3
    var q3 = ds_map_create();
    q3[? "pregunta"] = "¿Cuál era el nombre anterior de Bolivia?";
    q3[? "opcion1"] = "Nueva Granada";
    q3[? "opcion2"] = "Virreinato del Perú";
    q3[? "opcion3"] = "Alto Perú";
    q3[? "opcion4"] = "Provincia de La Paz";
    q3[? "respuesta"] = 3;
    ds_list_add(questions, q3);
    
    // Pregunta 4
    var q4 = ds_map_create();
    q4[? "pregunta"] = "¿Quién redactó el Acta de la Independencia de Bolivia?";
    q4[? "opcion1"] = "José Mariano Serrano";
    q4[? "opcion2"] = "Manuel Antonio Romero";
    q4[? "opcion3"] = "Casimiro Olañeta";
    q4[? "opcion4"] = "Gregorio Gutiérrez";
    q4[? "respuesta"] = 1;
    ds_list_add(questions, q4);
    
    // Pregunta 5
    var q5 = ds_map_create();
    q5[? "pregunta"] = "¿En qué ciudad se proclamó la independencia de Bolivia?";
    q5[? "opcion1"] = "La Paz";
    q5[? "opcion2"] = "Cochabamba";
    q5[? "opcion3"] = "Sucre (Chuquisaca)";
    q5[? "opcion4"] = "Santa Cruz";
    q5[? "respuesta"] = 3;
    ds_list_add(questions, q5);
    
    // Pregunta 6
    var q6 = ds_map_create();
    q6[? "pregunta"] = "¿Cuál fue la batalla más importante en la independencia de Bolivia?";
    q6[? "opcion1"] = "Batalla de Junín";
    q6[? "opcion2"] = "Batalla de Ayacucho";
    q6[? "opcion3"] = "Batalla de Chuquisaca";
    q6[? "opcion4"] = "Batalla de Laguna";
    q6[? "respuesta"] = 2;
    ds_list_add(questions, q6);
    
    // Pregunta 7
    var q7 = ds_map_create();
    q7[? "pregunta"] = "¿Cuántos años duró la guerra de independencia en Bolivia (Alto Perú)?";
    q7[? "opcion1"] = "3 años";
    q7[? "opcion2"] = "8 años";
    q7[? "opcion3"] = "15 años";
    q7[? "opcion4"] = "22 años";
    q7[? "respuesta"] = 4;
    ds_list_add(questions, q7);
    
    // Pregunta 8
    var q8 = ds_map_create();
    q8[? "pregunta"] = "¿Quién fue el general que liberó Bolivia del dominio español?";
    q8[? "opcion1"] = "José de San Martín";
    q8[? "opcion2"] = "Antonio José de Sucre";
    q8[? "opcion3"] = "Juan José Castelli";
    q8[? "opcion4"] = "Manuel Belgrano";
    q8[? "respuesta"] = 2;
    ds_list_add(questions, q8);
    
    // Pregunta 9
    var q9 = ds_map_create();
    q9[? "pregunta"] = "¿En qué fecha exacta se proclamó la independencia de Bolivia?";
    q9[? "opcion1"] = "5 de agosto de 1825";
    q9[? "opcion2"] = "6 de agosto de 1825";
    q9[? "opcion3"] = "7 de agosto de 1825";
    q9[? "opcion4"] = "8 de agosto de 1825";
    q9[? "respuesta"] = 2;
    ds_list_add(questions, q9);
    
    // Pregunta 10
    var q10 = ds_map_create();
    q10[? "pregunta"] = "¿Cuál fue el nombre original de la república creada en 1825?";
    q10[? "opcion1"] = "Bolivia";
    q10[? "opcion2"] = "República del Alto Perú";
    q10[? "opcion3"] = "República de Bolívar";
    q10[? "opcion4"] = "República de Sucre";
    q10[? "respuesta"] = 3;
    ds_list_add(questions, q10);
}

function get_question(index) {
    if (index >= 0 && index < ds_list_size(questions)) {
        return questions[| index];
    }
    return -1;
}

function clean_questions() {
    var i = 0;
    repeat (ds_list_size(questions)) {
        ds_map_destroy(questions[| i]);
        i++;
    }
    ds_list_destroy(questions);
}
```

---

## Script 2: scr_save_system
Sistema de guardado con archivos INI

```gml
function save_player_data(player_name, score, correct_answers) {
    var file_path = "jugadores.ini";
    
    ini_open(file_path);
    
    var best_score = ini_read_real(player_name, "mejor_puntaje", 0);
    var total_plays = ini_read_real(player_name, "total_partidas", 0);
    var total_correct = ini_read_real(player_name, "preguntas_correctas", 0);
    
    ini_write_string(player_name, "nombre", player_name);
    
    if (score > best_score) {
        ini_write_real(player_name, "mejor_puntaje", score);
    }
    
    ini_write_real(player_name, "total_partidas", total_plays + 1);
    ini_write_real(player_name, "preguntas_correctas", total_correct + correct_answers);
    
    ini_close();
}

function load_player_data(player_name) {
    var file_path = "jugadores.ini";
    
    ini_open(file_path);
    
    var data = ds_map_create();
    data[? "nombre"] = ini_read_string(player_name, "nombre", "No existe");
    data[? "mejor_puntaje"] = ini_read_real(player_name, "mejor_puntaje", 0);
    data[? "total_partidas"] = ini_read_real(player_name, "total_partidas", 0);
    data[? "preguntas_correctas"] = ini_read_real(player_name, "preguntas_correctas", 0);
    
    ini_close();
    
    return data;
}
```

---

## Objeto: obj_controller
**Create Event:**

```gml
player_name = "";
game_started = false;
init_questions();
```

**Clean Up Event:**

```gml
clean_questions();
```

---

## Objeto: obj_menu (Pantalla de Inicio)

**Create Event:**

```gml
player_input = "";
input_width = 300;
input_height = 40;
input_x = room_width / 2 - input_width / 2;
input_y = room_height / 2;
```

**Draw Event:**

```gml
draw_clear(c_white);
draw_set_color(c_black);
draw_set_font(fnt_title);
draw_text(room_width / 2, 50, "🇧🇴 INDEPENDENCIA DE BOLIVIA 🇧🇴");

draw_set_font(fnt_normal);
draw_text(room_width / 2, 150, "Cuestionario Educativo");

// Dibujar caja de entrada
draw_rectangle(input_x, input_y, input_x + input_width, input_y + input_height, false);
draw_set_color(c_black);
draw_rectangle(input_x, input_y, input_x + input_width, input_y + input_height, true);

draw_set_font(fnt_normal);
draw_text(input_x + 10, input_y + 10, player_input);

// Botón "Comenzar"
var btn_x = room_width / 2 - 75;
var btn_y = input_y + 80;
draw_rectangle(btn_x, btn_y, btn_x + 150, btn_y + 50, false);
draw_set_color(c_white);
draw_rectangle(btn_x, btn_y, btn_x + 150, btn_y + 50, true);
draw_set_color(c_black);
draw_text(btn_x + 75, btn_y + 25, "COMENZAR");

draw_set_color(c_black);
```

**Key Press Event:**

```gml
var key = keyboard_key;

if (key >= 32 && key <= 126 && string_length(player_input) < 20) {
    player_input += chr(key);
} else if (key == vk_backspace && string_length(player_input) > 0) {
    player_input = string_delete(player_input, string_length(player_input), 1);
} else if (key == vk_enter && string_length(player_input) > 0) {
    obj_controller.player_name = player_input;
    room_goto(rm_game);
}
```

**Left Released Event (Click):**

```gml
var mouse_x_pos = mouse_x;
var mouse_y_pos = mouse_y;
var btn_x = room_width / 2 - 75;
var btn_y = 280;

if (mouse_x_pos > btn_x && mouse_x_pos < btn_x + 150 &&
    mouse_y_pos > btn_y && mouse_y_pos < btn_y + 50 &&
    string_length(player_input) > 0) {
    obj_controller.player_name = player_input;
    room_goto(rm_game);
}
```

---

## Objeto: obj_game (Pantalla de Juego)

**Create Event:**

```gml
tiempo_total = 120;
tiempo_restante = tiempo_total;
pregunta_actual = 0;
puntaje = 0;
respuestas_correctas = 0;
tiempo_por_pregunta = 8;
preguntas_respondidas = 0;
```

**Step Event:**

```gml
tiempo_restante -= 1 / game_get_speed(gamespeed_framerate);

if (tiempo_restante <= 0) {
    tiempo_restante = 0;
    save_player_data(obj_controller.player_name, puntaje, respuestas_correctas);
    room_goto(rm_results);
}
```

**Draw Event:**

```gml
draw_clear(c_white);
draw_set_color(c_black);
draw_set_font(fnt_title);

draw_text(50, 20, "Jugador: " + obj_controller.player_name);
draw_text(room_width - 150, 20, "Puntaje: " + string(puntaje));

// Temporizador
draw_set_color(c_red);
var minutos = floor(tiempo_restante / 60);
var segundos = floor(tiempo_restante mod 60);
draw_text(room_width / 2 - 30, 20, string_format(minutos, 0, 0) + ":" + string_format(segundos, 2, 0));

draw_set_color(c_black);
draw_set_font(fnt_normal);

var q = get_question(pregunta_actual);

if (q != -1) {
    // Mostrar pregunta
    draw_text_ext(50, 100, q[? "pregunta"], 30, room_width - 100);
    
    // Mostrar opciones
    var opt_y = 180;
    var opcion_num = 1;
    repeat (4) {
        var opcion_text = "opcion" + string(opcion_num);
        draw_text(100, opt_y, string(opcion_num) + ". " + q[? opcion_text]);
        opt_y += 50;
        opcion_num++;
    }
}
```

**Key Press Event:**

```gml
var key = keyboard_key;
var q = get_question(pregunta_actual);

if (q != -1 && key >= ord("1") && key <= ord("4")) {
    var respuesta_usuario = key - ord("1") + 1;
    
    if (respuesta_usuario == q[? "respuesta"]) {
        puntaje += 10;
        respuestas_correctas++;
    }
    
    pregunta_actual++;
    
    if (pregunta_actual >= ds_list_size(questions)) {
        pregunta_actual = 0;
    }
}
```

---

## Objeto: obj_results (Pantalla de Resultados)

**Create Event:**

```gml
puntaje_final = obj_game.puntaje;
respuestas_correctas_final = obj_game.respuestas_correctas;
player_stats = load_player_data(obj_controller.player_name);
```

**Draw Event:**

```gml
draw_clear(c_white);
draw_set_color(c_black);
draw_set_font(fnt_title);

draw_text(room_width / 2, 40, "¡PARTIDA FINALIZADA!");

draw_set_font(fnt_normal);
draw_text(room_width / 2 - 100, 120, "Jugador: " + obj_controller.player_name);
draw_text(room_width / 2 - 100, 160, "Puntaje: " + string(puntaje_final));
draw_text(room_width / 2 - 100, 200, "Respuestas correctas: " + string(respuestas_correctas_final));
draw_text(room_width / 2 - 100, 240, "Mejor puntaje: " + string(player_stats[? "mejor_puntaje"]));
draw_text(room_width / 2 - 100, 280, "Total de partidas: " + string(player_stats[? "total_partidas"]));

// Botón "Reintentar"
var btn_x = room_width / 2 - 75;
var btn_y = room_height - 100;
draw_rectangle(btn_x, btn_y, btn_x + 150, btn_y + 50, false);
draw_set_color(c_white);
draw_rectangle(btn_x, btn_y, btn_x + 150, btn_y + 50, true);
draw_set_color(c_black);
draw_text(btn_x + 75, btn_y + 25, "REINTENTAR");
```

**Left Released Event (Click):**

```gml
var mouse_x_pos = mouse_x;
var mouse_y_pos = mouse_y;
var btn_x = room_width / 2 - 75;
var btn_y = room_height - 100;

if (mouse_x_pos > btn_x && mouse_x_pos < btn_x + 150 &&
    mouse_y_pos > btn_y && mouse_y_pos < btn_y + 50) {
    room_goto(rm_menu);
}
```

---

## 🔧 Instrucciones de Configuración

1. **Crea 2 fuentes en GameMaker:**
   - `fnt_title` (tamaño 32)
   - `fnt_normal` (tamaño 16)

2. **Crea 3 rooms:**
   - `rm_menu` (800x600)
   - `rm_game` (800x600)
   - `rm_results` (800x600)

3. **En cada room crea los objetos:**
   - `obj_controller` en `rm_menu` (marcado como "persistente")
   - `obj_menu` en `rm_menu`
   - `obj_game` en `rm_game`
   - `obj_results` en `rm_results`

4. **Copia y pega los códigos en los eventos correspondientes**

5. **Ejecuta el proyecto desde `rm_menu`**
