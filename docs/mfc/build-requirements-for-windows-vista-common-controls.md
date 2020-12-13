---
description: 'En savoir plus sur : spécifications de build pour les contrôles communs Windows'
title: Spécifications de build pour les contrôles communs Windows
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: 4d11b4da2fb1ff616ab077390c2d603e76382313
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339798"
---
# <a name="build-requirements-for-windows-common-controls"></a>Spécifications de build pour les contrôles communs Windows

La bibliothèque MFC (Microsoft Foundation Class) prend en charge les [contrôles communs Windows](/windows/win32/controls/common-controls-intro). Les contrôles communs sont inclus dans Windows et la bibliothèque est incluse dans Visual Studio. La bibliothèque MFC fournit de nouvelles méthodes qui améliorent les classes existantes, ainsi que des classes et des méthodes supplémentaires qui prennent en charge les contrôles communs Windows. Lorsque vous créez votre application, vous devez respecter les exigences de compilation et de migration décrites dans les sections suivantes.

## <a name="compilation-requirements"></a>Exigences de compilation

### <a name="supported-versions"></a>Versions prises en charge

MFC prend en charge toutes les versions des contrôles communs. Pour plus d’informations sur les versions des contrôles communs Windows, consultez [versions de contrôle courantes](/windows/win32/controls/common-control-versions).

### <a name="supported-character-sets"></a>Jeux de caractères pris en charge

Les contrôles communs Windows prennent uniquement en charge le jeu de caractères Unicode, et non le jeu de caractères ANSI. Si vous créez votre application à partir de la ligne de commande, utilisez les deux options du compilateur "define (/D)" suivantes pour spécifier Unicode en tant que jeu de caractères sous-jacent :

```
/D_UNICODE /DUNICODE
```

Si vous générez votre application dans l’environnement de développement intégré (IDE) de Visual Studio, spécifiez l’option de **jeu de caractères Unicode** de la propriété **jeu de caractères** dans le nœud **général** des propriétés du projet.

## <a name="migration-requirements"></a>Exigences de migration

Si vous utilisez l’IDE de Visual Studio pour générer une nouvelle application MFC qui utilise les contrôles communs Windows, l’IDE déclare automatiquement un manifeste approprié. Toutefois, si vous migrez une application MFC existante à partir de Visual Studio 2005 ou version antérieure et que vous souhaitez utiliser les contrôles communs, l’IDE ne fournit pas automatiquement les informations de manifeste pour mettre à niveau votre application. Au lieu de cela, vous devez insérer manuellement le code source suivant dans votre fichier d’en-tête précompilé :

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](general-mfc-topics.md)<br/>
[Graphique hiérarchique](hierarchy-chart.md)<br/>
[API ANSI déconseillées](deprecated-ansi-apis.md)
