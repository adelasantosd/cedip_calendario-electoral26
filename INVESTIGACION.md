# Nota de publicación

Documento de investigación recibido con los archivos originales. Las afirmaciones normativas y las fuentes que siguen no fueron revalidadas durante la preparación editorial de la versión 1.0.0. Los recuentos se ajustaron al JSON incluido.

# Investigación: calendario electoral y legislativo (corte 5 nov 2026)

Base de datos: [`datos/eventos.json`](datos/eventos.json). Tiene 93 eventos y cada uno incluye fecha, carril, fundamento, estado y fuentes.

## Cotejo con fuentes oficiales (5 nov 2026)
| Fuente | Versión consultada |
|---|---|
| Calendario integral INE/CG479/2026 | ine.mx, tabla "Actividades 2027" |
| Comunicados INE | centralelectoral.ine.mx |
| CPEUM | última reforma DOF 07-10-2026 |
| LGIPE | última reforma DOF 02-06-2026 |
| LGSMIME | última reforma DOF 14-11-2025 |
| LOCGEUM | última reforma DOF 07-07-2025 |
| Reglamento de la Cámara de Diputados (RCD) | última reforma DOF 07-05-2025 |
| LFPRH / LFRCF | DOF 09-04-2026 / 14-05-2026 |

Quedan 4 eventos con `verificar_primaria: true`: las comparecencias, cuya realización falta confirmar en la Gaceta, la estrategia de difusión y la intercampaña, que es una fecha inferida.

## Estados
`confirmado` = el acto ya ocurrió · `plazo_legal` = fecha fija en ley · `programado` = está en un acuerdo vigente · `estimado` = solo hay declaración política · `pendiente` = sin fecha.

## Hallazgos del cotejo
1. **La elección judicial ya no coincide con 2027.** Se movió a junio de 2028 (CPEUM, DOF 2 jun 2026). Las magistraturas de la Sala Superior del TEPJF que vencían en 2027 siguen hasta 2028.
2. **Nueva LGIPE de "Integridad en Candidaturas"** (DOF 2 jun 2026). Crea una comisión que revisa, de forma voluntaria y antes del registro, el riesgo de los perfiles de las candidaturas.
3. **Nueva causal de nulidad por intervención extranjera** (CPEUM art. 41 base VI, DOF 2 jun 2026).
4. **El sustituto en la presidencia del INE no se ratifica.** El art. 41 V-A ya fue cotejado: comité de 5 personas (3 de la Jucopo y 2 de la CNDH), luego 2/3 del Pleno, luego insaculación en el Pleno, luego insaculación en la SCJN. Quien resulte electo concluye el periodo hasta 2032. Antecedente: el 21 abr 2026 la Cámara designó con este procedimiento a 3 consejerías, entre ellas Blanca Y. Cruz García.
5. **El voto en el extranjero no cubre diputaciones federales** (LGIPE art. 329.1).
6. **El Reglamento de la Cámara, art. 184.2:** las iniciativas no dictaminadas se desechan al terminar la LXVI (31 ago 2027). La prórroga para dictaminar ya no tiene plazo fijo, porque los numerales 183.2-4 están derogados.

## Correcciones a la versión anterior
| Tema | Antes | Ahora |
|---|---|---|
| Fin de la Campaña Anual Intensa | 25 o 27 ene | **25 ene 2027** (INE) |
| Asignación de RP | 1-3 o 1-23 ago | **1-23 ago 2027** (tabla oficial) |
| Manifestación de intención de independientes | — | 5 oct-13 dic 2026. Rige la convocatoria; la tabla integral dice 30 nov |
| Reconsideración TEPJF | 26 ago | **19 ago** para cómputos distritales; 3 días antes de la instalación para el resto |
| Grupos parlamentarios | LOCGEUM art. 26 | **art. 14.4** |
| Revisión de la Cuenta Pública al 31 oct 2026 | CP 2025 | **CP 2024**. La CP 2025 vence el 31 oct 2027 |
| LIF | LFPRH fr. VIII | **fr. IV** |
| Plan B | DOF 23 o 24 abr | **23 abr 2026** |

## Altas (23 eventos nuevos)
Reimpresión de credencial, entrega de credenciales, lista nominal definitiva, validez del padrón, voto anticipado, observadores, designación de consejos distritales, SE/CAE, sorteos de mes y letra, plataformas electorales, casillas, Conóceles, paquetes, PREP y conteo rápido, reconsideraciones, designación de consejerías (abr 2026), tres reformas de 2026, Cuenta Pública 2025 y fin de la LXVI (RCD 184).

## Discrepancias que siguen abiertas
1. Inicio del PEF: el INE dice 10 sep; la LGIPE y la tabla oficial dicen "primera semana de septiembre".
2. Votación de la LIF en el Senado: 74-33 o 79 a favor.
3. Fecha de la votación de la presidencia del INE: 6-7 dic (según el diputado Ricardo Monreal, coordinador del GP MORENA) o 13-14 dic. Ambas son estimaciones; la convocatoria seguía sin emitirse al 3 nov.
4. Realización efectiva de las comparecencias de Hacienda (30 sep) y Salud (6 nov).

## Fuentes principales
- INE, calendario PEF 2026-2027: https://ine.mx/voto-y-elecciones/elecciones-2027/actividades-2027/
- INE, comunicado del calendario: https://centralelectoral.ine.mx/2026/07/31/planeara-y-organizara-ine-mas-de-500-actividades-del-proceso-electoral-federal-2026%E2%80%912027/
- INE, presidenta provisional: https://centralelectoral.ine.mx/2026/10/27/asegura-ine-continuidad-institucional-con-la-designacion-de-blanca-cruz-garcia-como-consejera-presidenta-provisional/
- INE, convocatoria de independientes: https://www.ine.mx/wp-content/uploads/2026/10/Anexo-1.-Convocatoria.pdf
- Leyes vigentes: https://www.diputados.gob.mx/LeyesBiblio/index.htm
- Zeta, Jucopo aplaza la convocatoria: https://zetatijuana.com/2026/11/jucopo-aplaza-convocatoria-para-la-presidencia-del-ine-van-27-renuncias/
- Heraldo, PEF 2027 en comisión: https://heraldodemexico.com.mx/nacional/2026/11/5/inicia-discusion-del-pef-2027-en-la-camara-de-diputados-2910983.html
