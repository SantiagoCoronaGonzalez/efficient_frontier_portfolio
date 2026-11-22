Frontera eficiente y prueba del CAPM en la BMV

Optimización de portafolios de media-varianza (Markowitz) y pruebas del CAPM con datos mensuales reales del mercado accionario mexicano. Todo está en un solo libro de Excel (Frontera_Sectores_rf_6.xlsx) y se calcula con fórmulas, sin macros ni complementos.

Proyecto para el curso de Finanzas Corporativas, CIDE.

Contenido

El análisis se hace a tres niveles:

7 sectores de la BMV (abr-2009 a sep-2026, 210 meses): Industrial, Materiales, Consumo frecuente, Salud, Telecomunicaciones, Financieros y Consumo no básico.
30 emisoras del S&P/BMV IPC (ago-2012 a sep-2026, 170 meses), que son las que tienen historia completa desde 2012.
Las mismas 30 emisoras con el modelo de un índice, usando el IPC como factor y rendimientos esperados de equilibrio (CAPM).
Estructura del libro
Hoja	Qué contiene
Datos	Capitalización por sector, INPC, CETES 364, inflación esperada e IPC (niveles mensuales)
Rend	Rendimientos mensuales reales por sector, inflación, tasa libre de riesgo real ex ante e IPC real
Cov	Matriz de varianzas y covarianzas de los sectores con encogimiento
Frontera	Frontera eficiente de los 7 sectores: portafolio de mínima varianza, portafolio tangente y línea del mercado de capitales (LMC)
CAPM_Sectores	Regresión del CAPM por sector y versión de Black (cero-beta)
DatosAcc	Precios ajustados mensuales de las 30 emisoras, INPC, CETES, inflación esperada e IPC
RendAcc	Rendimientos mensuales reales de las 30 emisoras
CovAcc	Matriz de varianzas y covarianzas de las acciones con encogimiento
FronteraAcc	Frontera eficiente de las 30 emisoras
CAPM_Acciones	Regresión del CAPM por emisora
CovIPC	Matriz de covarianzas implícita en el modelo de un índice
FronteraIPC	Frontera con el modelo de un índice y μ de equilibrio
Metodología

Rendimientos reales. Los rendimientos nominales se deflactan con el INPC: R_real = (P_t / P_{t-1}) / (1 + π_t) − 1.

Tasa libre de riesgo real ex ante. Se calcula con el CETES a 364 días y la mediana de la inflación esperada a 12 meses de la Encuesta de Expectativas de Banxico: rf = (1 + CETES) / (1 + π^e) − 1.

Encogimiento de la covarianza (Ledoit-Wolf). La covarianza muestral es muy ruidosa, así que se combina con una matriz objetivo de correlación constante: Σ* = δ·F + (1 − δ)·S. Los δ óptimos de Ledoit-Wolf son 0.2593 para los sectores y 0.6091 para las acciones.

Frontera analítica. Con los escalares A = 1'Σ⁻¹1, B = 1'Σ⁻¹μ, C = μ'Σ⁻¹μ y Δ = AC − B² se obtienen:

Portafolio de mínima varianza global: w_g = Σ⁻¹1 / A
Portafolio tangente: w_T ∝ Σ⁻¹(μ − rf)
Sharpe máximo: √(C − 2B·rf + A·rf²)

Se permiten posiciones cortas, por lo que los pesos pueden ser negativos.

Modelo de un índice. La covarianza se modela como Σ_ij = σ²_m·β_i·β_j, más σ²_ε,i en la diagonal. Con datos históricos, el rendimiento real del IPC (sin dividendos) queda por debajo de rf, y así no existe portafolio tangente. Por eso los μ se construyen con el CAPM, usando una prima de riesgo de mercado esperada de 6.69% (Damodaran, ene-2026: 4.23% de mercado maduro más 2.46% de riesgo país).

Prueba del CAPM. Para cada activo se estima por MCO: R_i − R^LR = α + β (R^IPC − R^LR) + ε, con la prueba H0: α = 0 al 5%. También se estima la versión de Black sin activo libre de riesgo, que da μ_z cero-beta.

Resultados principales
	Sectores	30 acciones	Modelo de un índice
rf real (anual)	2.43%	2.82%	2.82%
σ mínima varianza	11.2%	11.5%	10.2%
Sharpe máximo	0.63	1.32	0.45
CAPM por sector: ningún sector rechaza α = 0 (0 de 7). La β promedio es 0.78.
CAPM por acción: 6 de 30 emisoras rechazan α = 0. La β promedio es 0.99.
Black: la μ_z cero-beta estimada es 1.4% anual, frente a una rf real de 2.4%.

Aun con encogimiento, las fronteras con μ histórica dan portafolios tangentes con posiciones apalancadas y cortas muy grandes. Esto refleja el error de estimación en las medias, más que una estrategia aplicable. El modelo de un índice con μ de equilibrio da pesos mucho más razonables.

Fuentes de datos
Capitalización por sector: Banxico SIE, CF56 (millones de pesos)
INPC: Banxico SIE, CP154 (SP1)
CETES 364 días: Banxico SIE, CF107 (SF43945), promedio mensual de subastas
Inflación esperada a 12 meses: Encuesta de Expectativas de los Especialistas, Banxico CR155 (SR14195, mediana). Diciembre no tiene encuesta, así que se usa el dato de noviembre.
Precios de las emisoras e IPC (^MXX): Yahoo Finance, Adj Close mensual. Se excluyen KOFUBL, BBAJIOO, LACOMERUBC, Q y VOLARA porque empiezan a cotizar después de 2012.
Prima de riesgo de mercado: Damodaran, Country Risk Premiums (enero 2026)
Autor

Santiago Emiliano Corona Gonzalez, estudiante de Economía en el CIDE
