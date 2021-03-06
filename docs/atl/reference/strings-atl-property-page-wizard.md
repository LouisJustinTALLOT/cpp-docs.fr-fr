---
description: 'En savoir plus sur : chaînes, Assistant page de propriétés ATL'
title: Chaînes, Assistant Page de propriétés ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.strings
helpviewer_keywords:
- ATL Property Page Wizard, strings
ms.assetid: 00547db6-911f-49eb-92e1-2ba67079d4df
ms.openlocfilehash: f2d5b814cd817d37569765f4777c63661f6f8ca9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157644"
---
# <a name="strings-atl-property-page-wizard"></a>Chaînes, Assistant Page de propriétés ATL

::: moniker range="msvc-160"

L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

Fournit le texte associé à la page de propriétés.

- **Titre**

   Définit le texte qui apparaît sur l’onglet de la page de propriétés.

- **Chaîne doc**

   Définit une chaîne de texte décrivant la page. Cette chaîne peut être affichée dans la boîte de dialogue de la feuille de propriétés. Le cadre de propriété peut se servir de la description dans une ligne de statut ou une astuce. Actuellement, le cadre de propriété standard n’utilise pas cette chaîne.

- **Fichier d’aide**

   Définit le nom du fichier d’aide qui décrit comment utiliser la page de propriétés. Le nom ne doit pas comprendre de chemin d’accès. Lorsque l’utilisateur appuie sur **Aide**, le cadre ouvre le fichier d’aide dans le répertoire nommé dans la valeur de la clé HelpDir des entrées du registre de la page de propriétés sous son CLSID.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Options, Assistant Page de propriétés ATL](../../atl/reference/options-atl-property-page-wizard.md)
