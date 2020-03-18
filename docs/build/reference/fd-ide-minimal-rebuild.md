---
title: /FD (Régénération minimale IDE)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439806"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Régénération minimale IDE)

**/FD** est uniquement exposée aux utilisateurs dans la page de propriétés [ligne](command-line-property-pages.md) de C++ commande de la boîte de dialogue **pages de propriétés** d’un projet. Elle est disponible uniquement si l’option [/GM (activer la régénération minimale)](gm-enable-minimal-rebuild.md) déconseillée et désactivée par défaut n’est pas sélectionnée. **/FD** n’a aucun effet qu’à partir de l’environnement de développement. **/FD** n’est pas exposée dans la sortie de `cl /?`.

Si vous n’activez pas l’option **/GM** déconseillée dans l’environnement de développement, **/FD** est utilisé. **/FD** garantit que le fichier. IDB dispose d’informations de dépendance suffisantes. **/FD** est utilisé uniquement par l’environnement de développement, et il ne doit pas être utilisé à partir de la ligne de commande ou d’un script de génération.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
