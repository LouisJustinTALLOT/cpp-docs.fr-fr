---
description: 'En savoir plus sur : ressources localisées dans les applications MFC : dll satellites'
title: 'Ressources localisées dans des applications MFC : DLL satellites'
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: 4af771999c97af40ffe50399c77e91aec1af992a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176468"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Ressources localisées dans des applications MFC : DLL satellites

MFC version 7,0 et versions ultérieures offre une prise en charge améliorée des dll satellites, une fonctionnalité qui permet de créer des applications localisées pour plusieurs langues. Une DLL satellite est une [dll de ressources uniquement](creating-a-resource-only-dll.md) qui contient les ressources d’une application localisées pour une langue particulière. Au début de l’exécution de l’application, MFC charge automatiquement la ressource localisée la plus appropriée pour l’environnement. Par exemple, vous pouvez avoir une application avec des ressources en langue anglaise avec deux dll satellites, l’une contenant une traduction française de vos ressources et l’autre contenant une traduction en allemand. Lorsque l’application est exécutée sur un système en langue anglaise, elle utilise les ressources en anglais. Si elle est exécutée sur un système français, elle utilise les ressources françaises. Si elle est exécutée sur un système allemand, elle utilise les ressources allemandes.

Pour prendre en charge les ressources localisées dans une application MFC, MFC tente de charger une DLL satellite contenant des ressources localisées dans un langage spécifique. Les dll satellites sont nommées *ApplicationNameXXX*. dll, où *applicationName* est le nom du fichier. exe ou. dll à l’aide de MFC, et *xxx* est le code à trois lettres correspondant à la langue des ressources (par exemple, « fra » ou « DEU »).

MFC tente de charger la DLL de ressource pour chacune des langues suivantes dans l’ordre, en arrêtant quand elle en trouve une :

1. Langue de l’interface utilisateur par défaut de l’utilisateur actuel, telle qu’elle est retournée par l’API Win32 GetUserDefaultUILanguage ().

1. La langue de l’interface utilisateur par défaut de l’utilisateur actuel, sans sous-langue spécifique (c’est-à-dire ENC [canadien anglais] devient fra [États-Unis]).

1. Langue de l’interface utilisateur par défaut du système, telle qu’elle est retournée par l’API GetSystemDefaultUILanguage (). Sur les autres plateformes, il s’agit de la langue du système d’exploitation lui-même.

1. Langue de l’interface utilisateur par défaut du système, sans sous-langue spécifique.

1. Une fausse langue avec le code 3 lettres LOC.

Si MFC ne trouve pas de dll satellites, elle utilise toutes les ressources contenues dans l’application elle-même.

Par exemple, supposons qu’une application LangExample.exe utilise MFC et s’exécute sur un système à plusieurs interfaces utilisateur ; la langue de l’interface utilisateur système est fra [États-Unis] et la langue de l’interface utilisateur actuelle de l’utilisateur est définie sur FRC [canadien français]. MFC recherche les dll suivantes dans l’ordre suivant :

1. LangExampleFRC.dll (langue de l’interface utilisateur de l’utilisateur).

1. LangExampleFRA.dll (langue de l’interface utilisateur sans la sous-langue, dans cet exemple français (France).

1. LangExampleENU.dll (langue de l’interface utilisateur du système).

1. LangExampleLOC.dll.

Si aucune de ces dll n’est trouvée, MFC utilise les ressources de LangExample.exe.

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)<br/>
[TN057 : localisation des composants MFC](../mfc/tn057-localization-of-mfc-components.md)
