import tkinter as tk
from tkinter import ttk, messagebox

class App(tk.Tk):
    def __init__(self):
        super().__init__()

        # Configuración de la ventana
        self.title("Formulario - Elias Raphael")
        self.geometry("350x300")
        self.resizable(False, False)

        # ====== TÍTULO ======
        titulo = ttk.Label(self, text="Formulario - Elias Raphael", font=("Arial", 16))
        titulo.pack(pady=10)

        # ====== FRAME DEL FORMULARIO ======
        self.form_frame = ttk.Frame(self)
        self.form_frame.pack(pady=10, padx=20, fill="x")

        # ====== CAMPOS ======
        # Nombre
        ttk.Label(self.form_frame, text="Nombre:").grid(row=0, column=0, sticky="w", pady=5)
        self.entry_nombre = ttk.Entry(self.form_frame)
        self.entry_nombre.grid(row=0, column=1, pady=5)

        # Apellido
        ttk.Label(self.form_frame, text="Apellido:").grid(row=1, column=0, sticky="w", pady=5)
        self.entry_apellido = ttk.Entry(self.form_frame)
        self.entry_apellido.grid(row=1, column=1, pady=5)

        # Correo
        ttk.Label(self.form_frame, text="Correo:").grid(row=2, column=0, sticky="w", pady=5)
        self.entry_correo = ttk.Entry(self.form_frame)
        self.entry_correo.grid(row=2, column=1, pady=5)

        # Edad
        ttk.Label(self.form_frame, text="Edad:").grid(row=3, column=0, sticky="w", pady=5)
        self.entry_edad = ttk.Entry(self.form_frame)
        self.entry_edad.grid(row=3, column=1, pady=5)

        # ====== BOTÓN ======
        btn = ttk.Button(self, text="Aceptar", command=self.enviar)
        btn.pack(pady=10)

    def enviar(self):
        nombre = self.entry_nombre.get()
        apellido = self.entry_apellido.get()
        correo = self.entry_correo.get()
        edad = self.entry_edad.get()

        # --- Validación ---
        if not nombre or not apellido or not correo or not edad:
            messagebox.showwarning("Campos incompletos", "Todos los campos son obligatorios.")
            return
        
        if not edad.isdigit():
            messagebox.showerror("Edad inválida", "La edad debe ser un número.")
            return

        # --- Imprimir en consola ---
        print("=== DATOS DEL FORMULARIO ===")
        print("Nombre:", nombre)
        print("Apellido:", apellido)
        print("Correo:", correo)
        print("Edad:", edad)

# Ejecutar
if __name__ == "__main__":
    app = App()
    app.mainloop()
