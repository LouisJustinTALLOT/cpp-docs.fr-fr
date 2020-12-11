---
description: 'En savoir plus sur : technologie active et dll'
title: Technologie active et DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: 02a11bd18e8c6f62748d0be3f4cd708c8e4e4621
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157137"
---
# <a name="active-technology-and-dlls"></a>Technologie active et DLL

La technologie active permet l’implémentation complète de serveurs d’objets dans une DLL. Ce type de serveur est appelé serveur in-process. MFC ne prend pas entièrement en charge les serveurs in-process pour toutes les fonctionnalités de l’édition visuelle, principalement parce que la technologie active ne permet pas à un serveur de se raccorder à la boucle de message principale du conteneur. MFC requiert l’accès à la boucle de message de l’application conteneur pour gérer les touches accélérateur et le traitement du temps d’inactivité.

Si vous écrivez un serveur Automation et que votre serveur n’a pas d’interface utilisateur, vous pouvez faire de votre serveur un serveur in-process et le placer entièrement dans une DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Serveurs Automation](../mfc/automation-servers.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
