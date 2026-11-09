# Plantilla de email — Cuenta Clara · Sistema claro (estilo Nu)

Correo de bienvenida con lenguaje de **banca digital moderna**: lienzo claro, tipografía grande y segura, un bloque de color sólido como pieza central, mucho aire y cero decoración. Serio, premium y directo. No es una tarjeta con bordes suaves y cajas por todas partes.

HTML copia-pega: tablas semánticas, CSS inline y un bloque mínimo de `<style>` para responsive.

## Dirección de diseño

**Concepto:** "La cuenta, resuelta". Una sola idea por pantalla y una sola acción.

**La firma:** la banda teal a sangre (`#0F6B63`) con el resumen del mes. Es lo único saturado del correo; todo lo demás es blanco, negro y aire. El monto por persona va en oro grande — el único lugar donde aparece el oro además de la barra de marca y el logo.

### Tokens

| Rol | Valor | Uso |
| --- | --- | --- |
| Tinta | `#0A0F12` | Titulares y cifras |
| Tinta suave | `#4E5C63` | Párrafos |
| Tinta tenue | `#5A686E` | Cuerpo de apoyo |
| Meta | `#626F77` | Microcopy, footer |
| Papel | `#FFFFFF` | Lienzo del correo |
| Lavado | `#F3F7F6` | Cierre y footer |
| Borde | `#E2EAE8` | Hairlines |
| Marca | `#0F6B63` | Banda, botones, enlaces |
| Oro | `#F5B83D` / `#F5C05A` | Barra de marca y monto por persona |

**Tipografía:** Manrope (700/800) para titulares y cifras — geométrica, apretada, muy "producto financiero". DM Sans (400/500/700) para cuerpo. Sin monoespaciada: el dato se lee, no se descifra.

**Radios:** 24px contenedor, 100px botones. Las tarjetas no llevan sombra; la jerarquía se construye con color y aire.

### Estructura

1. Barra de marca (teal + oro)
2. Logo + mes
3. Hero: saludo, titular, subtítulo, CTA
4. **Banda teal** — resumen del mes y monto por persona
5. Detalle del reparto (ledger)
6. Cómo funciona (01 / 02 / 03)
7. Fila de confianza
8. Cierre sobre lavado: segundo CTA
9. P.D.
10. Footer claro

### Decisiones de UX

- **Una acción, un nombre.** "Crear mi cuenta" aparece dos veces con el mismo texto y el mismo destino; el usuario no tiene que decidir entre dos verbos distintos.
- **Jerarquía de un solo golpe.** El monto total y el monto por persona son lo más grande del correo, porque es lo único que el usuario quiere saber.
- **El detalle está, pero subordinado.** El ledger existe para dar credibilidad; nunca compite con el resumen.
- **Los pasos sí van numerados** porque son una secuencia real: sin el paso 1 no existe el 2. El número es información, no adorno.
- **Fricción explícita:** "Gratis · 3 minutos · sin tarjeta" justo bajo el botón, donde nace la duda.
- **Mobile primero de verdad:** el hero se apila, la banda reduce el monto a 36px, los pasos pasan a una columna y el botón ocupa todo el ancho.

## Archivos de marca

| Archivo | Uso |
| --- | --- |
| `logo-cuenta-clara.svg` | Vectorial animada (web / landing). |
| `logo-cuenta-clara-static.svg` | Vectorial estática (fuente del PNG y del base64). |
| `logo-cuenta-clara.png` | **352×352, fondo transparente.** Recomendada para envíos reales. |

**Opción A — la que viene por defecto:** logo embebido como `data:image/svg+xml;base64`. Se ve perfecto en Apple Mail, iOS, Outlook web y la vista previa del navegador, sin depender de hosting. Gmail y Outlook de escritorio pueden no mostrarlo.

**Opción B — producción:** sube `logo-cuenta-clara.png` a tu CDN y reemplaza el `src="data:image/svg+xml;base64,..."` en las **2** apariciones (header 38px, footer 24px) por:

```
<img src="https://tudominio.com/logo-cuenta-clara.png" width="38" height="38" alt="Cuenta Clara" style="display:block;border:0;border-radius:11px;">
```

Solo cambia el `src` y el `width`/`height` según la aparición. La altura de línea y el `border-radius` ya están puestos.

## Código

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html lang="es" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="x-apple-disable-message-reformatting">
  <meta name="format-detection" content="telephone=no,address=no,email=no,date=no,url=no">
  <meta name="color-scheme" content="light only">
  <meta name="supported-color-schemes" content="light">
  <title>Bienvenida a Cuenta Clara</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Manrope:wght@500;600;700;800&display=swap" rel="stylesheet">

  <!--[if mso]>
  <xml>
    <o:OfficeDocumentSettings>
      <o:AllowPNG/>
      <o:PixelsPerInch>96</o:PixelsPerInch>
    </o:OfficeDocumentSettings>
  </xml>
  <![endif]-->

  <style type="text/css">
    :root { color-scheme: light only; }

    body, table, td, a { -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
    table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
    table { border-collapse: collapse !important; }
    body { margin: 0 !important; padding: 0 !important; width: 100% !important; }
    a { text-decoration: none; }
    img { border: 0; display: block; outline: none; text-decoration: none; }
    p { margin: 0; }

    @media screen and (max-width: 620px) {
      .outer { padding: 18px 10px !important; }
      .shell { border-radius: 18px !important; }

      .hdr { padding: 20px 22px 0 22px !important; }
      .hero { padding: 30px 22px 26px 22px !important; }
      .h1 { font-size: 37px !important; line-height: 1.05 !important; letter-spacing: -1.3px !important; }
      .btn { display: block !important; text-align: center !important; padding-left: 18px !important; padding-right: 18px !important; }

      .band { padding: 26px 22px 24px 22px !important; }
      .band-total { font-size: 36px !important; letter-spacing: -1.2px !important; }
      .per-person { font-size: 27px !important; letter-spacing: -0.8px !important; }

      .detail { padding: 28px 22px 8px 22px !important; }
      .steps { padding: 26px 22px 28px 22px !important; }
      .step { display: block !important; width: 100% !important; padding: 16px 0 0 0 !important; }
      .step + .step { margin-top: 18px !important; }

      .trust { padding: 0 22px 30px 22px !important; }
      .closing { padding: 32px 22px !important; }
      .h2 { font-size: 26px !important; }
      .pd { padding: 20px 22px 22px 22px !important; }

      .footer { padding: 22px 22px 24px 22px !important; }
      .footer-col { display: block !important; width: 100% !important; text-align: left !important; }
      .footer-col + .footer-col { margin-top: 12px !important; }

      .hide-mobile { display: none !important; }
    }
  </style>
</head>

<body bgcolor="#EEF3F2" style="margin:0;padding:0;background-color:#EEF3F2;">

  <!-- Preheader -->
  <div style="display:none;font-size:1px;color:#EEF3F2;line-height:1px;max-height:0;max-width:0;opacity:0;overflow:hidden;mso-hide:all;">
    Reparte los gastos de la casa sin discutir. Crea tu cuenta gratis en 3 minutos.
    &#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;&#847;&zwnj;&nbsp;
  </div>

  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" bgcolor="#EEF3F2" style="background-color:#EEF3F2;">
    <tr>
      <td align="center" class="outer" style="padding:36px 12px;">

        <!--[if mso]>
        <table role="presentation" width="640" cellpadding="0" cellspacing="0" border="0"><tr><td>
        <![endif]-->

        <table role="presentation" class="shell" width="100%" cellpadding="0" cellspacing="0" border="0" bgcolor="#FFFFFF" style="width:100%;max-width:640px;background-color:#FFFFFF;border:1px solid #E2EAE8;border-radius:24px;overflow:hidden;">

          <!-- Barra de marca -->
          <tr>
            <td style="padding:0;font-size:0;line-height:0;">
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
                <tr>
                  <td width="92%" height="4" bgcolor="#0F6B63" style="width:92%;height:4px;line-height:4px;font-size:4px;background-color:#0F6B63;">&nbsp;</td>
                  <td width="8%" height="4" bgcolor="#F5B83D" style="width:8%;height:4px;line-height:4px;font-size:4px;background-color:#F5B83D;">&nbsp;</td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- 1. LOGO -->
          <tr>
            <td class="hdr" style="padding:24px 40px 0 40px;">
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
                <tr>
                  <td align="left" valign="middle">
                    <table role="presentation" cellpadding="0" cellspacing="0" border="0">
                      <tr>
                        <td width="38" height="38" align="center" valign="middle" style="width:38px;height:38px;">
                          <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0NCA0NCIgd2lkdGg9IjQ0IiBoZWlnaHQ9IjQ0IiByb2xlPSJpbWciIGFyaWEtbGFiZWw9IkN1ZW50YSBDbGFyYSI+CiAgPGRlZnM+CiAgICA8bGluZWFyR3JhZGllbnQgaWQ9InRlYWxHcmFkIiB4MT0iMCUiIHkxPSIwJSIgeDI9IjEwMCUiIHkyPSIxMDAlIj4KICAgICAgPHN0b3Agb2Zmc2V0PSIwJSIgc3RvcC1jb2xvcj0iIzBGNkI2MyIvPgogICAgICA8c3RvcCBvZmZzZXQ9IjEwMCUiIHN0b3AtY29sb3I9IiMwQTRBNDUiLz4KICAgIDwvbGluZWFyR3JhZGllbnQ+CiAgICA8cmFkaWFsR3JhZGllbnQgaWQ9ImNlbnRlckdsb3ciIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjUwJSI+CiAgICAgIDxzdG9wIG9mZnNldD0iMCUiIHN0b3AtY29sb3I9InJnYmEoMjU1LDI1NSwyNTUsMC4zNSkiLz4KICAgICAgPHN0b3Agb2Zmc2V0PSIxMDAlIiBzdG9wLWNvbG9yPSJyZ2JhKDI1NSwyNTUsMjU1LDApIi8+CiAgICA8L3JhZGlhbEdyYWRpZW50PgogIDwvZGVmcz4KICA8cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNDQiIGhlaWdodD0iNDQiIHJ4PSIxNCIgZmlsbD0idXJsKCN0ZWFsR3JhZCkiLz4KICA8cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNDQiIGhlaWdodD0iNDQiIHJ4PSIxNCIgZmlsbD0idXJsKCNjZW50ZXJHbG93KSIvPgogIAogIDwhLS0gRG9udXQgc2VnbWVudHMgLS0+CiAgPHBhdGggZD0iTTIyIDIgQzExIDIgMiAxMSAyIDIyIEMyIDI3LjUgNC41IDMyLjUgOC41IDM2IEwyMiAyMiBaIiBmaWxsPSIjRkZGRkZGIiBvcGFjaXR5PSIwLjk1Ii8+CiAgPHBhdGggZD0iTTIyIDIyIEwyNS41IDEwLjUiIHN0cm9rZT0icmdiYSgxNSwxMDYsOTksMC4zKSIgc3Ryb2tlLXdpZHRoPSIwLjUiIG9wYWNpdHk9IjAuNSIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMjUuNSAxMC41IEwzOC41IDguNSIgZmlsbD0iI0Y1QjgzRCIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMzguNSA4LjUiIHN0cm9rZT0icmdiYSgxNSwxMDYsOTksMC4zKSIgc3Ryb2tlLXdpZHRoPSIwLjUiIG9wYWNpdHk9IjAuNSIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMzguNSA4LjUgTDIyIDQyIiBmaWxsPSIjRkZGRkZGIiBvcGFjaXR5PSIwLjUiLz4KICA8cGF0aCBkPSJNMjIgMjIgTDIyIDQyIiBzdHJva2U9InJnYmEoMTUsMTA2LDk5LDAuMykiIHN0cm9rZS13aWR0aD0iMC41IiBvcGFjaXR5PSIwLjUiLz4KICAKICA8Y2lyY2xlIGN4PSIyMiIgY3k9IjIyIiByPSIzLjUiIGZpbGw9IiNGNUI4M0QiLz4KICA8Y2lyY2xlIGN4PSIyMiIgY3k9IjIyIiByPSI2IiBmaWxsPSJub25lIiBzdHJva2U9InJnYmEoMTUsMTA2LDk5LDAuNikiIHN0cm9rZS13aWR0aD0iMS41Ii8+Cjwvc3ZnPg==" width="38" height="38" alt="Cuenta Clara" style="display:block;border:0;border-radius:11px;">
                        </td>
                        <td style="padding-left:10px;font:800 20px/1.2 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;letter-spacing:-0.4px;">
                          Cuenta Clara
                        </td>
                      </tr>
                    </table>
                  </td>
                  <td align="right" valign="middle" class="hide-mobile" style="font:600 11px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;letter-spacing:1.2px;text-transform:uppercase;">
                    Marzo 2026
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- 2. HERO -->
          <tr>
            <td class="hero" style="padding:40px 40px 34px 40px;">
              <p style="margin:0 0 16px 0;font:500 16px/1.5 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#5A686E;">Hola, Ana</p>

              <h1 class="h1" style="margin:0 0 18px 0;font:800 54px/1.02 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-2px;color:#0A0F12;">
                Reparte los gastos<br>sin discutir.
              </h1>

              <p style="margin:0 0 28px 0;font:400 17px/1.6 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#4E5C63;max-width:440px;">
                Sube la factura del arriendo, la luz o el mercado. Nosotros calculamos cuánto le toca a cada uno.
              </p>

              <!--[if mso]>
              <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" href="https://cuentaclara.example/registro" style="height:54px;v-text-anchor:middle;width:210px;" arcsize="50%" stroke="f" fillcolor="#0F6B63">
                <w:anchorlock/>
                <center style="color:#FFFFFF;font-family:'Segoe UI',Arial,sans-serif;font-size:16px;font-weight:bold;">Crear mi cuenta</center>
              </v:roundrect>
              <![endif]-->

              <!--[if !mso]><!-- -->
              <a href="https://cuentaclara.example/registro" class="btn" style="display:inline-block;padding:17px 32px;border-radius:100px;background-color:#0F6B63;color:#FFFFFF;font:700 16px/1.2 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;text-decoration:none;mso-hide:all;">Crear mi cuenta</a>
              <!--<![endif]-->

              <p style="margin:16px 0 0 0;font:500 13px/1.5 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;">
                Gratis&nbsp;&nbsp;·&nbsp;&nbsp;3 minutos&nbsp;&nbsp;·&nbsp;&nbsp;sin tarjeta
              </p>
            </td>
          </tr>

          <!-- 3. BANDA TEAL — RESUMEN -->
          <tr>
            <td class="band" bgcolor="#0F6B63" style="padding:30px 40px 28px 40px;background-color:#0F6B63;">
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
                <tr>
                  <td style="font:700 11px/1.3 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.4px;text-transform:uppercase;color:#CFE2DF;">Resumen de marzo</td>
                  <td align="right" style="font:600 12px/1.3 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#CFE2DF;">Ejemplo &middot; 4 personas</td>
                </tr>
              </table>

              <div class="band-total" style="margin-top:14px;font:800 46px/1 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-1.8px;color:#FFFFFF;">
                $2.400.000
              </div>
              <div style="margin-top:9px;font:400 13px/1.5 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#CFE2DF;">
                Total de 3 gastos compartidos
              </div>

              <!-- Barra de reparto: 4 partes iguales -->
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:20px;">
                <tr>
                  <td width="24.25%" height="6" bgcolor="#A9D6CF" style="width:24.25%;height:6px;line-height:6px;font-size:0;background-color:#A9D6CF;">&nbsp;</td>
                  <td width="1%" height="6" style="width:1%;height:6px;line-height:6px;font-size:0;">&nbsp;</td>
                  <td width="24.25%" height="6" bgcolor="#A9D6CF" style="width:24.25%;height:6px;line-height:6px;font-size:0;background-color:#A9D6CF;">&nbsp;</td>
                  <td width="1%" height="6" style="width:1%;height:6px;line-height:6px;font-size:0;">&nbsp;</td>
                  <td width="24.25%" height="6" bgcolor="#A9D6CF" style="width:24.25%;height:6px;line-height:6px;font-size:0;background-color:#A9D6CF;">&nbsp;</td>
                  <td width="1%" height="6" style="width:1%;height:6px;line-height:6px;font-size:0;">&nbsp;</td>
                  <td width="24.25%" height="6" bgcolor="#A9D6CF" style="width:24.25%;height:6px;line-height:6px;font-size:0;background-color:#A9D6CF;">&nbsp;</td>
                </tr>
              </table>

              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:10px;">
                <tr>
                  <td style="font:600 10px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.1px;text-transform:uppercase;color:#CFE2DF;">4 partes iguales</td>
                  <td align="right" style="font:600 10px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.1px;text-transform:uppercase;color:#CFE2DF;">25% cada una</td>
                </tr>
              </table>

              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:20px;">
                <tr>
                  <td height="1" bgcolor="#2E8077" style="height:1px;font-size:0;line-height:0;background-color:#2E8077;">&nbsp;</td>
                </tr>
              </table>

              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:16px;">
                <tr>
                  <td valign="bottom" style="font:700 11px/1.3 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.4px;text-transform:uppercase;color:#CFE2DF;padding-bottom:4px;">
                    <span style="color:#F5C05A;">&#9632;</span>&nbsp; A cada uno
                  </td>
                  <td align="right" class="per-person" style="font:800 34px/1 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-1.2px;color:#F5C05A;">
                    $600.000
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- 4. DETALLE -->
          <tr>
            <td class="detail" style="padding:34px 40px 10px 40px;">
              <p style="margin:0;font:700 11px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.4px;text-transform:uppercase;color:#0F6B63;">El detalle</p>

              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:6px;">
                <tr>
                  <td style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:500 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#26313A;">Arriendo</td>
                  <td align="right" style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:600 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;">$1.800.000</td>
                </tr>
                <tr>
                  <td style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:500 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#26313A;">Internet</td>
                  <td align="right" style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:600 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;">$120.000</td>
                </tr>
                <tr>
                  <td style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:500 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#26313A;">Mercado</td>
                  <td align="right" style="padding:15px 0;border-bottom:1px solid #E8EEEB;font:600 15px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;">$480.000</td>
                </tr>
                <tr>
                  <td style="padding:16px 0 0 0;font:700 11px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.2px;text-transform:uppercase;color:#626F77;">Total del mes</td>
                  <td align="right" style="padding:16px 0 0 0;font:800 17px/1.4 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;">$2.400.000</td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- 5. CÓMO FUNCIONA -->
          <tr>
            <td class="steps" style="padding:30px 40px 34px 40px;">
              <p style="margin:0;font:700 11px/1.4 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.4px;text-transform:uppercase;color:#0F6B63;">Cómo funciona</p>

              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" style="margin-top:6px;">
                <tr>
                  <td class="step" width="33.33%" valign="top" style="width:33.33%;padding:18px 20px 0 0;border-top:2px solid #0A0F12;">
                    <div style="font:800 12px/1 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.6px;color:#0F6B63;">01</div>
                    <div style="margin-top:10px;font:700 17px/1.3 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-0.3px;color:#0A0F12;">Crea el grupo</div>
                    <p style="margin:6px 0 0 0;font:400 14px/1.55 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#5A686E;">Ponle nombre a la casa e invita a quien vive ahí.</p>
                  </td>
                  <td class="step" width="33.33%" valign="top" style="width:33.33%;padding:18px 20px 0 20px;border-top:2px solid #0A0F12;">
                    <div style="font:800 12px/1 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.6px;color:#0F6B63;">02</div>
                    <div style="margin-top:10px;font:700 17px/1.3 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-0.3px;color:#0A0F12;">Registra los gastos</div>
                    <p style="margin:6px 0 0 0;font:400 14px/1.55 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#5A686E;">Sube la factura o escribe el monto y elige cómo se reparte.</p>
                  </td>
                  <td class="step" width="33.33%" valign="top" style="width:33.33%;padding:18px 0 0 20px;border-top:2px solid #0A0F12;">
                    <div style="font:800 12px/1 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:1.6px;color:#0F6B63;">03</div>
                    <div style="margin-top:10px;font:700 17px/1.3 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-0.3px;color:#0A0F12;">Cierra el mes</div>
                    <p style="margin:6px 0 0 0;font:400 14px/1.55 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#5A686E;">Cada uno ve qué pagó, qué debe y cuánto transferir.</p>
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- 6. CONFIANZA -->
          <tr>
            <td class="trust" align="center" style="padding:0 40px 38px 40px;">
              <p style="margin:0;font:500 12px/1.6 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;">
                Datos cifrados <span style="color:#626F77;">&nbsp;·&nbsp;</span> Soporte humano <span style="color:#626F77;">&nbsp;·&nbsp;</span> Sin costo de mantención
              </p>
            </td>
          </tr>

          <!-- 7. CIERRE / CTA -->
          <tr>
            <td class="closing" align="center" bgcolor="#F3F7F6" style="padding:40px;background-color:#F3F7F6;border-top:1px solid #E2EAE8;">
              <h2 class="h2" style="margin:0 0 10px 0;font:800 30px/1.14 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;letter-spacing:-1px;color:#0A0F12;">
                Tu casa, en orden<br>desde hoy.
              </h2>
              <p style="margin:0 0 22px 0;font:400 15px/1.6 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#4E5C63;">
                Crear la cuenta toma 3 minutos y no pide tarjeta.
              </p>

              <!--[if mso]>
              <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" href="https://cuentaclara.example/registro" style="height:54px;v-text-anchor:middle;width:210px;" arcsize="50%" stroke="f" fillcolor="#0F6B63">
                <w:anchorlock/>
                <center style="color:#FFFFFF;font-family:'Segoe UI',Arial,sans-serif;font-size:16px;font-weight:bold;">Crear mi cuenta</center>
              </v:roundrect>
              <![endif]-->

              <!--[if !mso]><!-- -->
              <a href="https://cuentaclara.example/registro" class="btn" style="display:inline-block;padding:17px 32px;border-radius:100px;background-color:#0F6B63;color:#FFFFFF;font:700 16px/1.2 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;text-decoration:none;mso-hide:all;">Crear mi cuenta</a>
              <!--<![endif]-->

              <p style="margin:14px 0 0 0;font:500 12px/1.5 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;">
                Puedes invitar a todos cuando quieras.
              </p>
            </td>
          </tr>

          <!-- 8. P.D. -->
          <tr>
            <td class="pd" align="center" style="padding:22px 40px 26px 40px;">
              <p style="margin:0;font:400 13px/1.65 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#5A686E;">
                <strong style="font-weight:700;color:#0A0F12;">P.D.</strong> Responde este correo y te contesta una persona del equipo.
              </p>
            </td>
          </tr>

          <!-- 9. FOOTER -->
          <tr>
            <td class="footer" bgcolor="#F3F7F6" style="padding:26px 40px 30px 40px;background-color:#F3F7F6;border-top:1px solid #E2EAE8;">
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
                <tr>
                  <td class="footer-col" width="55%" valign="middle" style="width:55%;">
                    <table role="presentation" cellpadding="0" cellspacing="0" border="0">
                      <tr>
                        <td width="24" height="24" align="center" valign="middle" style="width:24px;height:24px;">
                          <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0NCA0NCIgd2lkdGg9IjQ0IiBoZWlnaHQ9IjQ0IiByb2xlPSJpbWciIGFyaWEtbGFiZWw9IkN1ZW50YSBDbGFyYSI+CiAgPGRlZnM+CiAgICA8bGluZWFyR3JhZGllbnQgaWQ9InRlYWxHcmFkIiB4MT0iMCUiIHkxPSIwJSIgeDI9IjEwMCUiIHkyPSIxMDAlIj4KICAgICAgPHN0b3Agb2Zmc2V0PSIwJSIgc3RvcC1jb2xvcj0iIzBGNkI2MyIvPgogICAgICA8c3RvcCBvZmZzZXQ9IjEwMCUiIHN0b3AtY29sb3I9IiMwQTRBNDUiLz4KICAgIDwvbGluZWFyR3JhZGllbnQ+CiAgICA8cmFkaWFsR3JhZGllbnQgaWQ9ImNlbnRlckdsb3ciIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjUwJSI+CiAgICAgIDxzdG9wIG9mZnNldD0iMCUiIHN0b3AtY29sb3I9InJnYmEoMjU1LDI1NSwyNTUsMC4zNSkiLz4KICAgICAgPHN0b3Agb2Zmc2V0PSIxMDAlIiBzdG9wLWNvbG9yPSJyZ2JhKDI1NSwyNTUsMjU1LDApIi8+CiAgICA8L3JhZGlhbEdyYWRpZW50PgogIDwvZGVmcz4KICA8cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNDQiIGhlaWdodD0iNDQiIHJ4PSIxNCIgZmlsbD0idXJsKCN0ZWFsR3JhZCkiLz4KICA8cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNDQiIGhlaWdodD0iNDQiIHJ4PSIxNCIgZmlsbD0idXJsKCNjZW50ZXJHbG93KSIvPgogIAogIDwhLS0gRG9udXQgc2VnbWVudHMgLS0+CiAgPHBhdGggZD0iTTIyIDIgQzExIDIgMiAxMSAyIDIyIEMyIDI3LjUgNC41IDMyLjUgOC41IDM2IEwyMiAyMiBaIiBmaWxsPSIjRkZGRkZGIiBvcGFjaXR5PSIwLjk1Ii8+CiAgPHBhdGggZD0iTTIyIDIyIEwyNS41IDEwLjUiIHN0cm9rZT0icmdiYSgxNSwxMDYsOTksMC4zKSIgc3Ryb2tlLXdpZHRoPSIwLjUiIG9wYWNpdHk9IjAuNSIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMjUuNSAxMC41IEwzOC41IDguNSIgZmlsbD0iI0Y1QjgzRCIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMzguNSA4LjUiIHN0cm9rZT0icmdiYSgxNSwxMDYsOTksMC4zKSIgc3Ryb2tlLXdpZHRoPSIwLjUiIG9wYWNpdHk9IjAuNSIvPgogIDxwYXRoIGQ9Ik0yMiAyMiBMMzguNSA4LjUgTDIyIDQyIiBmaWxsPSIjRkZGRkZGIiBvcGFjaXR5PSIwLjUiLz4KICA8cGF0aCBkPSJNMjIgMjIgTDIyIDQyIiBzdHJva2U9InJnYmEoMTUsMTA2LDk5LDAuMykiIHN0cm9rZS13aWR0aD0iMC41IiBvcGFjaXR5PSIwLjUiLz4KICAKICA8Y2lyY2xlIGN4PSIyMiIgY3k9IjIyIiByPSIzLjUiIGZpbGw9IiNGNUI4M0QiLz4KICA8Y2lyY2xlIGN4PSIyMiIgY3k9IjIyIiByPSI2IiBmaWxsPSJub25lIiBzdHJva2U9InJnYmEoMTUsMTA2LDk5LDAuNikiIHN0cm9rZS13aWR0aD0iMS41Ii8+Cjwvc3ZnPg==" width="24" height="24" alt="" aria-hidden="true" style="display:block;border:0;border-radius:7px;">
                        </td>
                        <td style="padding-left:8px;font:800 15px/1.2 Manrope,'Segoe UI',Helvetica,Arial,sans-serif;color:#0A0F12;letter-spacing:-0.2px;">Cuenta Clara</td>
                      </tr>
                    </table>
                  </td>
                  <td class="footer-col" width="45%" align="right" valign="middle" style="width:45%;font:500 12px/1.7 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;">
                    <a href="https://cuentaclara.example/preferencias" style="color:#0F6B63;text-decoration:none;">Preferencias</a>
                    <span style="color:#626F77;">&nbsp;·&nbsp;</span>
                    <a href="https://cuentaclara.example/baja" style="color:#0F6B63;text-decoration:none;">Cancelar suscripción</a>
                  </td>
                </tr>
              </table>

              <p style="margin:16px 0 0 0;font:400 12px/1.6 'DM Sans','Segoe UI',Helvetica,Arial,sans-serif;color:#626F77;">
                &copy; 2026 Cuenta Clara &nbsp;·&nbsp; Bogotá, Colombia &nbsp;·&nbsp;
                <a href="https://cuentaclara.example" style="color:#626F77;text-decoration:none;">cuentaclara.example</a>
              </p>
            </td>
          </tr>

        </table>

        <!--[if mso]>
        </td></tr></table>
        <![endif]-->

      </td>
    </tr>
  </table>

</body>
</html>
```

## Qué personalizar

1. **Nombre:** reemplaza `Hola, Ana` por tu variable (`{{first_name}}`, `{{name}}`).
2. **Mes:** `Marzo 2026` aparece en el header y dentro de la banda.
3. **Cifras:** `$2.400.000`, `$600.000` y las tres filas del ledger deben cuadrar entre sí (total ÷ personas). La etiqueta `Ejemplo · 4 personas` marca que los datos son de muestra; si el correo va a un usuario real, cámbiala por `Tus datos` y usa sus cifras.
4. **Enlaces:** reemplaza `https://cuentaclara.example/...` por las URLs reales.
5. **Logo:** ver *Archivos de marca*.

## Pegar la plantilla en EmailJS

Este archivo es **independiente**: la landing no lo carga ni lo referencia. Solo sirve para copiar y pegar.

1. Abre **EmailJS → Email Templates → tu plantilla** (`template_9s5xlpi`).
2. En la pestaña **Content**, cambia a modo **HTML** y pega el archivo `email-cuenta-clara.html` completo (desde `<!DOCTYPE html>` hasta `</html>`). No lo recortes: el bloque `<style>` del `<head>` contiene las reglas de móvil.
3. En **Settings** de la plantilla:
   - **To Email:** `{{email}}`
   - **From Name:** `Cuenta Clara`
   - **From Email:** *Use Default Email Address*
   - **Reply To:** `samuel.ramirezb@uniagustiniana.edu.co`
4. Guarda y prueba desde la landing. El formulario envía `{ email: "..." }`, que es la única variable que la plantilla necesita para resolver el destinatario.

> El cuerpo del correo no usa variables `{{ }}`: el saludo y las cifras son contenido fijo. Si quieres personalizarlo, `{{email}}` también está disponible dentro del HTML (por ejemplo, en la línea de preheader), porque llega como parámetro del envío.

## Notas técnicas

- Tablas con `role="presentation"`, CSS inline y `color-scheme: light only` para que los clientes no inviertan el diseño a oscuro.
- **Manrope + DM Sans** se cargan por `<link>` a Google Fonts: funciona en Apple Mail, iOS y la vista previa del navegador. Gmail y Outlook ignoran la carga y caen a `Segoe UI` / `Helvetica` / `Arial`, que mantienen la jerarquía aunque cambie el carácter tipográfico.
- La banda teal va a sangre dentro del contenedor redondeado (`overflow:hidden` hace el recorte en clientes modernos; Outlook muestra esquinas rectas y no se rompe nada).
- CTA "bulletproof": VML para Outlook de escritorio, `<a>` con `mso-hide:all` para el resto.
- Sin imágenes de fondo, sin degradados, sin sombras: nada que Outlook tenga que degradar.
- Contenedor de `640px`; en móvil (< 620px) el hero se apila, los pasos pasan a una columna y el botón ocupa todo el ancho.
- Antes de producción: versión en texto plano y prueba en Gmail, Outlook desktop, Apple Mail e iOS/Android.
