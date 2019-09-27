# Initializing the Canvas

Let's take a closer look at 'fn init'.

'main.rs'

```rust

// this function initializes the canvas
fn init<'a>(width: i32, height: i32) -> (Canvas<Window>, EventPump) {
    let sdl_context = sdl2::init().unwrap();
    let video_subsystem = sdl_context.video().unwrap();

    let window = video_subsystem
        .window("Rusty Snake", width as u32 + 1, height as u32 + 1)
        .position_centered()
        .build()
        .unwrap();

    let mut canvas = window.into_canvas().present_vsync().build().unwrap();

    canvas.set_draw_color(Color::RGB(0, 0, 0));
    canvas.clear();
    canvas.present();

    let event_pump = sdl_context.event_pump().unwrap();
    (canvas, event_pump)
}

```
 'fn' declares the function, 'init' is its name. '<'a>' indicates its lifetime. Lifetimes are unique to rust, declaring them is not needed for most functions, so we will just acknowledge its existence, but ignore it for now. The function takes two parameters, x and y. Rust is a type safe language, so the types of the parameters need to be indicated. In this example, the type of both parameters is 'i32', a 32bit integer. The return types also need to be specifically named. 'fn init' returns two values in a bracket, separated by a comma. The types of these values are defined in the sdl2-crate. We'll ignore the body of the function for now.

1. In 'main()', delete the 'println!' statement.
2. Declare the variables 'canvas_width' and 'canvas_height'. Values?
3. Call the function by adding the following line:
'let (mut canvas, mut events) = init(canvas_width, canvas_height);'
4. Add the following lines:
```
loop {
      for event in events.poll_iter() {
          // handle user input here
      }
```
4. Hit 'cargo run'. What happens?