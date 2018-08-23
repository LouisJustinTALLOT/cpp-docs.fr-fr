---
title: Configuration requise pour les contrôles communs Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8d3e5c8cd6b4a0876d0cac8e1fb3c7e87eed9cc
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538675"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Configuration requise pour les contrôles communs Windows Vista
La bibliothèque Microsoft Foundation Class (MFC) prend en charge la version 6.1 des contrôles communs Windows. Les contrôles communs sont inclus dans Windows Vista et la bibliothèque est incluse dans le SDK Visual Studio. La bibliothèque fournit de nouvelles méthodes qui améliorent les classes existantes et de nouvelles classes et méthodes qui prennent en charge les contrôles communs Windows Vista. Lorsque vous créez votre application, vous devez respecter les exigences de compilation et de migration décrites dans les sections suivantes.  
  
## <a name="compilation-requirements"></a>Spécifications de compilation  
  
### <a name="supported-versions"></a>Versions prises en charge  
 Certaines nouvelles classes et les méthodes prennent en charge uniquement Windows Vista et versions ultérieures, alors qu’autres méthodes prennent également en charge les systèmes d’exploitation antérieurs. Une note dans la `Requirements` section de chaque rubrique de la méthode spécifie que lorsque la valeur minimale requise de système d’exploitation est Windows Vista.  
  
 Même si votre ordinateur n’exécute pas Windows Vista, vous pouvez créer une application MFC qui s’exécute sur Windows Vista, si vous avez les fichiers d’en-tête MFC version 6.1 sur votre ordinateur. Toutefois, les contrôles communs qui sont conçues spécifiquement pour Windows Vista fonctionnent uniquement sur ce système et sont ignorés par les systèmes d’exploitation antérieurs.  
  
### <a name="supported-character-sets"></a>Jeux de caractères pris en charge  
 Les nouveaux contrôles communs Windows ne prennent en charge que le jeu de caractères Unicode, et non le jeu de caractères ANSI. Si vous créez votre application à partir de la ligne de commande, utilisez les deux options du compilateur "define (/D)" suivantes pour spécifier Unicode en tant que jeu de caractères sous-jacent :  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 Si vous générez votre application dans l’environnement de développement intégré (IDE) Visual Studio, spécifiez la **jeu de caractères Unicode** possibilité du **du jeu de caractères** propriété dans le **général**  nœud des propriétés du projet.  
  
 La version ANSI de plusieurs méthodes MFC ont été déconseillées à compter de la version 6.1 des contrôles communs Windows. Pour plus d’informations, consultez [API de ANSI déconseillées](../mfc/deprecated-ansi-apis.md).  
  
## <a name="migration-requirements"></a>Exigences de migration  
 Si vous utilisez l'IDE de Visual Studio pour créer une application MFC qui utilise la version 6.1 des contrôles communs Windows, l'IDE déclare automatiquement un manifeste approprié. Toutefois, si vous migrez une application existante de MFC depuis une version antérieure de Visual Studio et que voulez utiliser les nouveaux contrôles communs, l'IDE ne fournira pas automatiquement les informations du manifeste pour mettre à niveau votre application. Au lieu de cela, vous devez insérer manuellement le code source suivant dans votre **stdafx.h** fichier :  
  
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
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)   
 [Graphique hiérarchique](../mfc/hierarchy-chart.md)   
 [API ANSI dépréciées](../mfc/deprecated-ansi-apis.md)

