
# Base de hechos del cliente

estado_cliente = {
    "ingresos": 60000,
    "historial": "Excelente",
    "deuda_activa": 12000,
    "tiene_avalista": True
}


# 2. MOTOR DE INFERENCIA
def motor_evaluacion_credito(hechos):

    # Regla de rechazo absoluto
    if hechos["deuda_activa"] > 10000 and not hechos["tiene_avalista"]:
        return "RECHAZADO: Alto riesgo por deuda sin aval."

    # Regla de aprobación
    if hechos["ingresos"] > 50000 and hechos["historial"] == "Excelente":
        return "APROBADO: Cumple criterios Hipotecario Plus."

    # Regla por defecto
    return "EN REVISIÓN MANUAL: No cumple criterios automáticos."


# 3. EJECUCIÓN
decision = motor_evaluacion_credito(estado_cliente)

print("=== SISTEMA EXPERTO DE CRÉDITO ===")
print("Veredicto:", decision)
