=============================
Factura Electrónica Argentina
=============================

.. !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! This file is generated by oca-gen-addon-readme !!
   !! changes will be overwritten.                   !!
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

.. |badge1| image:: https://img.shields.io/badge/maturity-Beta-yellow.png
    :target: https://odoo-community.org/page/development-status
    :alt: Beta
.. |badge2| image:: https://img.shields.io/badge/licence-AGPL--3-blue.png
    :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
    :alt: License: AGPL-3
.. |badge3| image:: https://img.shields.io/badge/github-OCA%2Fl10n--argentina-lightgray.png?logo=github
    :target: https://github.com/OCA/l10n-argentina/tree/14.0/l10n_ar_afipws_fe
    :alt: OCA/l10n-argentina
.. |badge4| image:: https://img.shields.io/badge/weblate-Translate%20me-F47D42.png
    :target: https://translation.odoo-community.org/projects/l10n-argentina-14-0/l10n-argentina-14-0-l10n_ar_afipws_fe
    :alt: Translate me on Weblate
.. |badge5| image:: https://img.shields.io/badge/runbot-Try%20me-875A7B.png
    :target: https://runbot.odoo-community.org/runbot/179/14.0
    :alt: Try me on Runbot

|badge1| |badge2| |badge3| |badge4| |badge5| 

Integration of Argentinian AFIP Webservices

This module integrates the electronic invoice webservices and system adaptations for Argentina usage.
This module integrates the following webservices:

* "wsfev1": Webservice de factura electronica mercado interno (incluye factura MiPyme)
* "wsfex1": Webservice de factura electronica de exportacion
* "wsbfe1": Webservice de bonos fiscales electronicos

**Table of contents**

.. contents::
   :local:

Known issues / Roadmap
======================

* Integracion de webserice de facturacion con detalle de items "WSMTXCA"
* Integrar la recuperacion de cotizacion de dolar desde el webservice de AFIP
* Permitir seleccionar el env de homologacion y produccion desde settings
* Si la factura se valido en homologacion y no en prod, mostrar un ribbon
* Integrar metodo ConsultarComprobante e integrarlo en los comprobantes de compra para comprobar su validez
* Mejorar el retorno de los metodos informativos del journal
* Deprecar la libreria "pyafipws" y realizar una integracion nativa del webservice de AFIP, para evitar mapeos inecesarios.

Changelog
=========

14.0.1.0.0 (2023-01-29)
~~~~~~~~~~~~~~~~~~~~~~~

* Refactorizacion completa del modulo y de sus metodos
* Se elimina necesidad de utilizar secuencias individuales para la numeracion de comprobantes, se usa las de odoo nativo
* Numeracion a prueba de fallos, integrado reproceso para recuperar CAE en caso de falta de conecciones
* Decoracion visual de numero de comprobante, para en la ux ofrecer informacion al usuario sobre el estado de AFIP del comprobantes
* Se mejoraron las vistas y su usabilidad
* Ahora es posible en caso de desincronizacion o probelmas con un comprobante, forzar su numero de cbte para recuperar los datos de AFIP.
* Se eliminaron metodos sin usar y codigo legacy
* Se crearon nuevos metodos builders y archivos por webservice, para mejor mantenimiento del codigo

14.0.1.0.1 (2023-02-23)
~~~~~~~~~~~~~~~~~~~~~~~
- Solo se permite forzar el número de comprobante en facturas de venta, si el usuario está en modo debug y si hay una desincronización de secuencias. Esto es útil para reparar errores de secuencias directamente desde la UI.
- Se agrega pyafipws al manifest y requirements para que la instalación de la librería sea automática.
- Se eliminan raise error en los mensajes de error XML. De esta forma, el mensaje de error se guarda en afip_message. El usuario puede entrar al registro y consultar el error. Esto es útil cuando se autorizan múltiples facturas.
- FIX: Solo se muestran los decoradores de errores de secuencia en facturas de venta
- FIX: Solo se muestra la pestaña AFIP si el comprobante es de venta. TODO: Luego al implementar la validación automática de comprobantes de venta contra AFIP se volverá a mostrar la tab.
- No se muestra mas la tab de "EDI" ya que esta localización no usa la funcionalidad EDI de odoo.

Bug Tracker
===========

Bugs are tracked on `GitHub Issues <https://github.com/OCA/l10n-argentina/issues>`_.
In case of trouble, please check there if your issue has already been reported.
If you spotted it first, help us smashing it by providing a detailed and welcomed
`feedback <https://github.com/OCA/l10n-argentina/issues/new?body=module:%20l10n_ar_afipws_fe%0Aversion:%2014.0%0A%0A**Steps%20to%20reproduce**%0A-%20...%0A%0A**Current%20behavior**%0A%0A**Expected%20behavior**>`_.

Do not contact contributors directly about support or help with technical issues.

Credits
=======

Authors
~~~~~~~

* Nimarosa
* ADHOC SA
* Moldeo Interactive
* Exemax
* Codize

Contributors
~~~~~~~~~~~~

- Nimarosa
- ADHOC S.A.
- Modeo Interactive
- Exemax
- Codize

Maintainers
~~~~~~~~~~~

This module is maintained by the OCA.

.. image:: https://odoo-community.org/logo.png
   :alt: Odoo Community Association
   :target: https://odoo-community.org

OCA, or the Odoo Community Association, is a nonprofit organization whose
mission is to support the collaborative development of Odoo features and
promote its widespread use.

.. |maintainer-nimarosa| image:: https://github.com/nimarosa.png?size=40px
    :target: https://github.com/nimarosa
    :alt: nimarosa
.. |maintainer-ibuioli| image:: https://github.com/ibuioli.png?size=40px
    :target: https://github.com/ibuioli
    :alt: ibuioli

Current `maintainers <https://odoo-community.org/page/maintainer-role>`__:

|maintainer-nimarosa| |maintainer-ibuioli| 

This module is part of the `OCA/l10n-argentina <https://github.com/OCA/l10n-argentina/tree/14.0/l10n_ar_afipws_fe>`_ project on GitHub.

You are welcome to contribute. To learn how please visit https://odoo-community.org/page/Contribute.
