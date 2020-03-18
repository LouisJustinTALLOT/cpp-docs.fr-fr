---
title: Options DUMPBIN
description: Guide de référence des options de ligne de commande de l’utilitaire Microsoft DUMPBIN.
ms.date: 02/09/2020
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 54f5a22808026f4442f85d5e53a0805702e05868
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440043"
---
# <a name="dumpbin-options"></a>Options DUMPBIN

Une option se compose d’un *spécificateur d’option*, qui est un tiret (`-`) ou une barre oblique (`/`), suivi du nom de l’option. Les noms d’options ne peuvent pas être abrégés. Certaines options prennent des arguments, spécifiés après un signe deux-points (`:`). Aucun espace ou onglet n’est autorisé dans une spécification d’option. Utilisez un ou plusieurs espaces ou tabulations pour séparer les spécifications de l’option sur la ligne de commande. Les noms d’options et leurs arguments de mot clé ou de nom de fichier ne respectent pas la casse. La plupart des options s’appliquent à tous les fichiers binaires, mais certaines s’appliquent uniquement à certains types de fichiers. Par défaut, DUMPBIN envoie des informations à la sortie standard. Utilisez l’option [/out](out-dumpbin.md) pour envoyer la sortie vers un fichier.

## <a name="options-list"></a>Liste d’options

DUMPBIN offre les options suivantes :

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[: {octets\|nooctets}\]](disasm.md)

- [/errorreport : {None | INVITE | File d’attente | SEND}](errorreport-dumpbin-exe.md) (déconseillé)

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[: filename\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[: {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT : NomFichier](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[: VERBOSe\]](pdbpath.md)

- [/RANGEE : vaMin\[, vaMax\]](range.md)

- [/RAWDATA\[: {NONE\|1\|2\|4\|8}\[, #\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION : nom](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

Pour répertorier les options prises en charge par DUMPBIN sur la ligne de commande, utilisez l’option **/ ?** option.

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)\
\ de [ligne de commande DUMPBIN](dumpbin-command-line.md)
[Référence DUMPBIN](dumpbin-reference.md)
