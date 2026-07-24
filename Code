import tkinter as tk
from tkinter import messagebox
from PIL import Image, ImageTk


# ==========================================================
# NODO DEL ÁRBOL
# ==========================================================

class Nodo:

    def __init__(self, valor):
        self.valor = valor
        self.izquierdo = None
        self.derecho = None
        # Coordenadas asignadas al momento de graficar
        self.x = 0
        self.y = 0


# ==========================================================
# ÁRBOL BINARIO DE BÚSQUEDA
# ==========================================================

class ArbolBinario:

    NIVEL_MAXIMO = 4

    def __init__(self):
        self.raiz = None

    # ------------------------------------------------------
    # INSERTAR
    # ------------------------------------------------------

    def insertar(self, valor):

        if self.raiz is None:
            self.raiz = Nodo(valor)
            return

        actual = self.raiz
        nivel_actual = 1

        while True:

            if valor == actual.valor:
                raise ValueError(f"El valor {valor} ya existe en el árbol")

            elif valor < actual.valor:

                if actual.izquierdo is None:

                    if nivel_actual + 1 > self.NIVEL_MAXIMO:
                        raise ValueError("No puede exceder 4 niveles")

                    actual.izquierdo = Nodo(valor)
                    return

                actual = actual.izquierdo

            else:

                if actual.derecho is None:

                    if nivel_actual + 1 > self.NIVEL_MAXIMO:
                        raise ValueError("No puede exceder 4 niveles")

                    actual.derecho = Nodo(valor)
                    return

                actual = actual.derecho

            nivel_actual += 1

    # ------------------------------------------------------
    # BUSCAR (devuelve booleano)
    # ------------------------------------------------------

    def buscar(self, valor):
        return self.buscar_nodo(valor) is not None

    # ------------------------------------------------------
    # BUSCAR NODO (devuelve el nodo encontrado, o None)
    # Se usa para poder resaltarlo gráficamente en el canvas.
    # ------------------------------------------------------

    def buscar_nodo(self, valor):

        actual = self.raiz

        while actual is not None:

            if valor == actual.valor:
                return actual

            elif valor < actual.valor:
                actual = actual.izquierdo

            else:
                actual = actual.derecho

        return None

    # ------------------------------------------------------
    # RECORRIDOS
    # ------------------------------------------------------

    def preorden(self):

        resultado = []

        def _recorrer(nodo):
            if nodo is not None:
                resultado.append(nodo.valor)
                _recorrer(nodo.izquierdo)
                _recorrer(nodo.derecho)

        _recorrer(self.raiz)
        return resultado

    def inorden(self):

        resultado = []

        def _recorrer(nodo):
            if nodo is not None:
                _recorrer(nodo.izquierdo)
                resultado.append(nodo.valor)
                _recorrer(nodo.derecho)

        _recorrer(self.raiz)
        return resultado

    def posorden(self):

        resultado = []

        def _recorrer(nodo):
            if nodo is not None:
                _recorrer(nodo.izquierdo)
                _recorrer(nodo.derecho)
                resultado.append(nodo.valor)

        _recorrer(self.raiz)
        return resultado

    # ------------------------------------------------------
    # LIMPIAR
    # ------------------------------------------------------

    def limpiar(self):
        self.raiz = None


# ==========================================================
# LOGIN
# ==========================================================

class Login:

    # ==========================================
    # Fecha de elaboración del proyecto.
    # Se deja fija (no usa la fecha del sistema) para que el
    # formulario siempre muestre la fecha real de elaboración,
    # sin importar el día en que se ejecute la aplicación.
    # ==========================================
    FECHA_ELABORACION = "23/07/2026"

    def __init__(self):

        # ==========================================
        # CONFIGURACIÓN DE LA VENTANA
        # ==========================================

        self.ventana = tk.Tk()
        self.ventana.title("Fase4_HailyenGrajales")
        self.ventana.geometry("520x650")
        self.ventana.resizable(False, False)
        self.ventana.configure(bg="#0F172A")

        # Centrar ventana

        ancho = 520
        alto = 650

        pantalla_ancho = self.ventana.winfo_screenwidth()
        pantalla_alto = self.ventana.winfo_screenheight()

        x = int((pantalla_ancho / 2) - (ancho / 2))
        y = int((pantalla_alto / 2) - (alto / 2))

        self.ventana.geometry(f"{ancho}x{alto}+{x}+{y}")

        # ==========================================
        # TARJETA PRINCIPAL
        # ==========================================

        self.tarjeta = tk.Frame(
            self.ventana,
            bg="#1E293B",
            bd=0
        )

        self.tarjeta.place(
            relx=0.5,
            rely=0.5,
            anchor="center",
            width=430,
            height=590
        )

        # ==========================================
        # LOGO
        # ==========================================

        try:

            imagen = Image.open("arbol.png")
            imagen = imagen.resize((140, 140))

            self.logo = ImageTk.PhotoImage(imagen)

            tk.Label(
                self.tarjeta,
                image=self.logo,
                bg="#1E293B"
            ).pack(pady=(20, 10))

        except Exception:

            tk.Label(
                self.tarjeta,
                text="🌳",
                font=("Segoe UI Emoji", 52),
                bg="#1E293B",
                fg="#22C55E"
            ).pack(pady=(20, 10))

        # ==========================================
        # TITULOS
        # ==========================================

        tk.Label(
            self.tarjeta,
            text="ÁRBOL BINARIO DE BÚSQUEDA",
            font=("Bahnschrift", 18, "bold"),
            fg="white",
            bg="#1E293B"
        ).pack()

        tk.Label(
            self.tarjeta,
            text="Formulario de Inicio de Sesión",
            font=("Segoe UI", 10),
            fg="#94A3B8",
            bg="#1E293B"
        ).pack(pady=(0, 20))

        # ==========================================
        # INFORMACIÓN
        # ==========================================

        self.informacion = tk.Frame(
            self.tarjeta,
            bg="#1E293B"
        )

        self.informacion.pack()

        # ==========================================
        # DATOS DE LA APLICACIÓN
        # ==========================================

        tk.Label(
            self.informacion,
            text="Aplicación: Árboles Binarios",
            font=("Segoe UI", 11),
            bg="#1E293B",
            fg="white"
        ).pack(pady=4)

        tk.Label(
            self.informacion,
            text="Estudiante: Hailyen Jullieth Grajales",
            font=("Segoe UI", 10),
            bg="#1E293B",
            fg="white"
        ).pack()

        # Fecha fija de elaboración (no depende de la fecha del
        # sistema en el momento de la ejecución).

        tk.Label(
            self.informacion,
            text=f"Fecha: {self.FECHA_ELABORACION}",
            font=("Segoe UI", 10),
            bg="#1E293B",
            fg="#CBD5E1"
        ).pack(pady=4)

        # ==========================================
        # CONTRASEÑA
        # ==========================================

        tk.Label(
            self.informacion,
            text="Contraseña",
            font=("Segoe UI", 11, "bold"),
            bg="#1E293B",
            fg="white"
        ).pack(pady=(20, 6))

        self.txt_password = tk.Entry(
            self.informacion,
            font=("Segoe UI", 12),
            justify="center",
            show="●",
            width=24,
            bd=0,
            relief="flat"
        )

        self.txt_password.pack(ipady=7)
        self.txt_password.focus_set()
        self.txt_password.bind("<Return>", lambda event: self.validar())

        # ==========================================
        # BOTONES
        # ==========================================

        self.panel_botones = tk.Frame(
            self.informacion,
            bg="#1E293B"
        )

        self.panel_botones.pack(pady=25)

        self.btn_ingresar = tk.Button(
            self.panel_botones,
            text="🔐 Ingresar",
            font=("Segoe UI", 10, "bold"),
            bg="#2563EB",
            fg="white",
            activebackground="#1D4ED8",
            activeforeground="white",
            relief="flat",
            width=14,
            cursor="hand2",
            command=self.validar
        )

        self.btn_ingresar.grid(row=0, column=0, padx=6)

        self.btn_salir = tk.Button(
            self.panel_botones,
            text="❌ Salir",
            font=("Segoe UI", 10, "bold"),
            bg="#DC2626",
            fg="white",
            activebackground="#B91C1C",
            activeforeground="white",
            relief="flat",
            width=14,
            cursor="hand2",
            command=self.ventana.destroy
        )

        self.btn_salir.grid(row=0, column=1, padx=6)

        self.btn_acerca = tk.Button(
            self.informacion,
            text="ℹ Acerca de",
            font=("Segoe UI", 10, "bold"),
            bg="#0F766E",
            fg="white",
            activebackground="#115E59",
            activeforeground="white",
            relief="flat",
            width=32,
            cursor="hand2",
            command=self.acerca_de
        )

        self.btn_acerca.pack(pady=10)

        # ==========================================
        # EFECTO HOVER
        # ==========================================

        self.hover(self.btn_ingresar, "#2563EB", "#1D4ED8")
        self.hover(self.btn_salir, "#DC2626", "#B91C1C")
        self.hover(self.btn_acerca, "#0F766E", "#115E59")

        # ==========================================
        # PIE DE PÁGINA
        # ==========================================

        tk.Label(
            self.tarjeta,
            text="Universidad Nacional Abierta y a Distancia - UNAD",
            font=("Segoe UI", 9),
            bg="#1E293B",
            fg="#94A3B8"
        ).pack(side="bottom", pady=12)

        self.ventana.mainloop()

    # ==========================================
    # EFECTO HOVER
    # ==========================================

    def hover(self, boton, color_normal, color_hover):

        boton.bind(
            "<Enter>",
            lambda event: boton.config(bg=color_hover)
        )

        boton.bind(
            "<Leave>",
            lambda event: boton.config(bg=color_normal)
        )

    # ==========================================
    # ACERCA DE
    # ==========================================

    def acerca_de(self):

        messagebox.showinfo(
            "Acerca de",
            "Árbol Binario de Búsqueda\n\n"
            "Curso: Estructura de Datos\n"
            "Universidad Nacional Abierta y a Distancia - UNAD\n\n"
            "Desarrollado por:\n"
            "Hailyen Jullieth Grajales Quiñonez"
        )

    # ==========================================
    # VALIDAR LOGIN
    # ==========================================

    def validar(self):

        contraseña = self.txt_password.get().strip().upper()

        if contraseña == "ARBOL":

            self.ventana.destroy()

            VentanaPrincipal()

        else:

            messagebox.showerror(
                "Acceso denegado",
                "La contraseña ingresada es incorrecta."
            )

            self.txt_password.delete(0, tk.END)
            self.txt_password.focus_set()


# ==========================================================
# VENTANA PRINCIPAL
# ==========================================================

class VentanaPrincipal:

    # Colores usados para graficar los nodos del árbol
    COLOR_NODO = "#A5F3FC"
    COLOR_BORDE = "#0E7490"
    COLOR_LINEA = "#334155"
    COLOR_TEXTO = "#0F172A"

    # Colores usados para resaltar el nodo encontrado con
    # "Buscar Nodo"
    COLOR_NODO_RESALTADO = "#FDE047"
    COLOR_BORDE_RESALTADO = "#CA8A04"

    def __init__(self):

        self.arbol = ArbolBinario()

        # Valor actualmente resaltado en el canvas (resultado de
        # una búsqueda exitosa). None si no hay nada resaltado.
        self.valor_resaltado = None

        self.ventana = tk.Tk()

        self.ventana.title("Árbol Binario de Búsqueda")

        self.ventana.geometry("1000x720")
        self.ventana.minsize(800, 600)

        self.ventana.configure(bg="#0F172A")

        # La ventana ahora puede redimensionarse: al cambiar de
        # tamaño, la distribución de los nodos se recalcula
        # automáticamente (ver evento <Configure> del canvas).
        self.ventana.resizable(True, True)

        # ==========================================
        # ENCABEZADO
        # ==========================================

        encabezado = tk.Frame(
            self.ventana,
            bg="#1E3A5F",
            height=70
        )

        encabezado.pack(fill="x")

        tk.Label(
            encabezado,
            text="🌳 ÁRBOL BINARIO DE BÚSQUEDA",
            font=("Bahnschrift", 20, "bold"),
            bg="#1E3A5F",
            fg="white"
        ).pack(pady=(12, 0))

        tk.Label(
            encabezado,
            text="Curso Estructura de Datos - UNAD",
            font=("Segoe UI", 10),
            bg="#1E3A5F",
            fg="#D6E4F0"
        ).pack()

        # ==========================================
        # PANEL SUPERIOR
        # ==========================================

        superior = tk.Frame(
            self.ventana,
            bg="#0F172A"
        )

        superior.pack(fill="x", pady=15)

        tk.Label(
            superior,
            text="Valor del Nodo",
            font=("Segoe UI", 11, "bold"),
            bg="#0F172A",
            fg="white"
        ).grid(row=0, column=0, padx=10)

        self.txt_nodo = tk.Entry(
            superior,
            width=15,
            justify="center",
            font=("Segoe UI", 12)
        )

        self.txt_nodo.grid(row=0, column=1, padx=8)
        self.txt_nodo.bind("<Return>", lambda event: self.agregar_nodo())

        # ==========================================
        # BOTONES
        # ==========================================

        self.btn_agregar = tk.Button(
            superior,
            text="Agregar Nodo",
            bg="#2563EB",
            fg="white",
            font=("Segoe UI", 10, "bold"),
            width=14,
            relief="flat",
            cursor="hand2",
            command=self.agregar_nodo
        )

        self.btn_agregar.grid(row=0, column=2, padx=6)

        self.btn_buscar = tk.Button(
            superior,
            text="Buscar Nodo",
            bg="#16A34A",
            fg="white",
            font=("Segoe UI", 10, "bold"),
            width=14,
            relief="flat",
            cursor="hand2",
            command=self.buscar_nodo
        )

        self.btn_buscar.grid(row=0, column=3, padx=6)

        self.btn_limpiar = tk.Button(
            superior,
            text="Limpiar",
            bg="#F59E0B",
            fg="white",
            font=("Segoe UI", 10, "bold"),
            width=12,
            relief="flat",
            cursor="hand2",
            command=self.limpiar_arbol
        )

        self.btn_limpiar.grid(row=0, column=4, padx=6)

        self.btn_salir = tk.Button(
            superior,
            text="Salir",
            bg="#DC2626",
            fg="white",
            font=("Segoe UI", 10, "bold"),
            width=10,
            relief="flat",
            cursor="hand2",
            command=self.ventana.destroy
        )

        self.btn_salir.grid(row=0, column=5, padx=6)

        # ==========================================
        # PANEL GRÁFICO DEL ÁRBOL
        # ==========================================

        self.paneles = tk.Frame(
            self.ventana,
            bg="#0F172A"
        )

        self.paneles.pack(fill="both", expand=True, padx=15, pady=10)

        self.canvas = tk.Canvas(
            self.paneles,
            bg="white",
            highlightthickness=1,
            highlightbackground="#334155"
        )

        self.canvas.pack(fill="both", expand=True)

        # Redibuja el árbol automáticamente cuando el usuario
        # cambia el tamaño de la ventana / del canvas.
        self.canvas.bind("<Configure>", lambda event: self.dibujar_arbol())

        # ==========================================
        # PANEL DE RECORRIDOS
        # ==========================================
        # Cada recorrido se muestra en un Entry más grande, con su
        # propia barra de desplazamiento horizontal DEBAJO (en su
        # propia fila de la grilla, no superpuesta), de modo que
        # sea claramente visible y utilizable aunque el árbol
        # tenga los 4 niveles completos y el texto sea largo.

        panel_recorridos = tk.Frame(
            self.ventana,
            bg="#0F172A"
        )

        panel_recorridos.pack(fill="x", padx=15, pady=(0, 15))

        self.txt_preorden = self._crear_campo_recorrido(
            panel_recorridos, "Preorden", fila=0
        )

        self.txt_inorden = self._crear_campo_recorrido(
            panel_recorridos, "Inorden", fila=1
        )

        self.txt_posorden = self._crear_campo_recorrido(
            panel_recorridos, "Posorden", fila=2
        )

        panel_recorridos.grid_columnconfigure(1, weight=1)

        self.ventana.mainloop()

    # ==========================================
    # CREAR CAMPO DE RECORRIDO CON SCROLL HORIZONTAL
    # ==========================================

    def _crear_campo_recorrido(self, contenedor, etiqueta, fila):

        # Cada recorrido ocupa DOS filas reales de la grilla:
        #   fila_base      -> el campo de texto (Entry)
        #   fila_base + 1  -> la barra de desplazamiento horizontal
        # Esto evita que el Entry y el Scrollbar se encimen o se
        # vean recortados, como ocurría al compartir la misma fila.

        fila_base = fila * 2

        tk.Label(
            contenedor,
            text=etiqueta,
            font=("Segoe UI", 11, "bold"),
            bg="#0F172A",
            fg="white",
            width=9,
            anchor="w"
        ).grid(
            row=fila_base, column=0, rowspan=2,
            sticky="w", padx=(0, 10)
        )

        entry = tk.Entry(
            contenedor,
            font=("Consolas", 12),
            state="readonly",
            readonlybackground="white",
            fg="#0F172A",
            relief="solid",
            bd=1
        )

        scrollbar = tk.Scrollbar(
            contenedor,
            orient="horizontal",
            command=entry.xview,
            width=16,
            bg="#64748B",
            troughcolor="#CBD5E1",
            activebackground="#1D4ED8"
        )

        entry.config(xscrollcommand=scrollbar.set)

        entry.grid(
            row=fila_base, column=1,
            sticky="ew", ipady=6, pady=(6, 0)
        )

        scrollbar.grid(
            row=fila_base + 1, column=1,
            sticky="ew", pady=(2, 6)
        )

        return entry

    # ==========================================
    # AGREGAR NODO
    # ==========================================

    def agregar_nodo(self):

        texto = self.txt_nodo.get().strip()

        if texto == "":
            messagebox.showerror("Error", "Ingrese un número entero")
            return

        try:
            valor = int(texto)

        except ValueError:
            messagebox.showerror("Error", "Ingrese un número entero")
            self.txt_nodo.delete(0, tk.END)
            self.txt_nodo.focus_set()
            return

        try:
            self.arbol.insertar(valor)

        except ValueError as error:
            mensaje = str(error)

            if "4 niveles" in mensaje:
                messagebox.showerror("Error", "No puede exceder 4 niveles")
            else:
                messagebox.showerror("Error", mensaje)

            self.txt_nodo.delete(0, tk.END)
            self.txt_nodo.focus_set()
            return

        # Al agregar un nodo se limpia cualquier resaltado previo
        self.valor_resaltado = None

        self.txt_nodo.delete(0, tk.END)
        self.txt_nodo.focus_set()

        self.actualizar_vista()

    # ==========================================
    # BUSCAR NODO
    # ==========================================

    def buscar_nodo(self):

        texto = self.txt_nodo.get().strip()

        if texto == "":
            messagebox.showerror("Error", "Ingrese un número entero")
            return

        try:
            valor = int(texto)

        except ValueError:
            messagebox.showerror("Error", "Ingrese un número entero")
            self.txt_nodo.delete(0, tk.END)
            self.txt_nodo.focus_set()
            return

        nodo_encontrado = self.arbol.buscar_nodo(valor)

        if nodo_encontrado is not None:
            # Se guarda el valor encontrado para resaltarlo en
            # el canvas al redibujar el árbol.
            self.valor_resaltado = valor
            self.dibujar_arbol()
            messagebox.showinfo("Buscar Nodo", f"Valor {valor} encontrado en el árbol")
        else:
            self.valor_resaltado = None
            self.dibujar_arbol()
            messagebox.showinfo("Buscar Nodo", f"Valor {valor} no existe en el árbol")

        self.txt_nodo.delete(0, tk.END)
        self.txt_nodo.focus_set()

    # ==========================================
    # LIMPIAR
    # ==========================================

    def limpiar_arbol(self):

        self.arbol.limpiar()
        self.valor_resaltado = None
        self.canvas.delete("all")

        for entry in (self.txt_preorden, self.txt_inorden, self.txt_posorden):
            entry.config(state="normal")
            entry.delete(0, tk.END)
            entry.config(state="readonly")

        self.txt_nodo.delete(0, tk.END)
        self.txt_nodo.focus_set()

    # ==========================================
    # ACTUALIZAR RECORRIDOS Y GRÁFICO
    # ==========================================

    def actualizar_vista(self):

        self.actualizar_recorridos()
        self.dibujar_arbol()

    def actualizar_recorridos(self):

        pre = " ".join(str(v) for v in self.arbol.preorden())
        ino = " ".join(str(v) for v in self.arbol.inorden())
        pos = " ".join(str(v) for v in self.arbol.posorden())

        for entry, valor in (
            (self.txt_preorden, pre),
            (self.txt_inorden, ino),
            (self.txt_posorden, pos)
        ):
            entry.config(state="normal")
            entry.delete(0, tk.END)
            entry.insert(0, valor)
            entry.config(state="readonly")

    # ==========================================
    # DIBUJAR ÁRBOL EN EL CANVAS
    # ==========================================

    def dibujar_arbol(self):

        self.canvas.delete("all")

        if self.arbol.raiz is None:
            return

        ancho_canvas = self.canvas.winfo_width()
        alto_canvas = self.canvas.winfo_height()

        if ancho_canvas < 10:
            ancho_canvas = 960

        if alto_canvas < 10:
            alto_canvas = 380

        margen_x = 60
        margen_y = 50
        radio = 18

        espacio_y = (alto_canvas - 2 * margen_y) / max(self.arbol.NIVEL_MAXIMO - 1, 1)

        # ------------------------------------------------------
        # Se asignan las posiciones mediante subdivisión binaria
        # del ancho disponible: la raíz siempre queda centrada en
        # el canvas, cada hijo izquierdo se ubica en el centro de
        # la mitad izquierda del espacio de su padre y cada hijo
        # derecho en el centro de la mitad derecha. De esta forma
        # la raíz nunca se desplaza hacia un extremo, incluso en
        # árboles inclinados hacia un solo lado, y los
        # descendientes quedan distribuidos proporcionalmente
        # según el nivel, tal como se espera en la representación
        # gráfica de un ABB.
        # ------------------------------------------------------

        def asignar_posiciones(nodo, nivel, x_min, x_max):

            if nodo is None:
                return

            x_medio = (x_min + x_max) / 2

            nodo.x = x_medio
            nodo.y = margen_y + (nivel - 1) * espacio_y

            asignar_posiciones(nodo.izquierdo, nivel + 1, x_min, x_medio)
            asignar_posiciones(nodo.derecho, nivel + 1, x_medio, x_max)

        asignar_posiciones(self.arbol.raiz, 1, margen_x, ancho_canvas - margen_x)

        # Dibujar primero las líneas (conexiones)

        def dibujar_lineas(nodo):

            if nodo is None:
                return

            if nodo.izquierdo is not None:
                self.canvas.create_line(
                    nodo.x, nodo.y, nodo.izquierdo.x, nodo.izquierdo.y,
                    fill=self.COLOR_LINEA, width=2
                )

            if nodo.derecho is not None:
                self.canvas.create_line(
                    nodo.x, nodo.y, nodo.derecho.x, nodo.derecho.y,
                    fill=self.COLOR_LINEA, width=2
                )

            dibujar_lineas(nodo.izquierdo)
            dibujar_lineas(nodo.derecho)

        dibujar_lineas(self.arbol.raiz)

        # Dibujar los nodos (círculos) encima de las líneas.
        # El nodo cuyo valor coincide con el último resultado de
        # una búsqueda exitosa se resalta con otro color.

        def dibujar_nodos(nodo):

            if nodo is None:
                return

            resaltado = (
                self.valor_resaltado is not None
                and nodo.valor == self.valor_resaltado
            )

            color_relleno = self.COLOR_NODO_RESALTADO if resaltado else self.COLOR_NODO
            color_borde = self.COLOR_BORDE_RESALTADO if resaltado else self.COLOR_BORDE
            ancho_borde = 3 if resaltado else 2

            self.canvas.create_oval(
                nodo.x - radio, nodo.y - radio, nodo.x + radio, nodo.y + radio,
                fill=color_relleno, outline=color_borde, width=ancho_borde
            )

            self.canvas.create_text(
                nodo.x, nodo.y,
                text=str(nodo.valor),
                font=("Segoe UI", 10, "bold"),
                fill=self.COLOR_TEXTO
            )

            dibujar_nodos(nodo.izquierdo)
            dibujar_nodos(nodo.derecho)

        dibujar_nodos(self.arbol.raiz)


# ==========================================================
# PUNTO DE ENTRADA
# ==========================================================

if __name__ == "__main__":
    Login()
