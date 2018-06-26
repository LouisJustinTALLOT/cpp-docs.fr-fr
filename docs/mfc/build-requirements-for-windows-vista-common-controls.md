---
title: Configuration requise pour les contrôles communs Windows Vista | Documents Microsoft
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
ms.openlocfilehash: f8f167ac560fd8e2109c149f30841ecbe3c44fc8
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930974"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Configuration requise pour les contrôles communs Windows Vista
La bibliothèque Microsoft Foundation Class (MFC) prend en charge la version 6.1 des contrôles communs Windows. Les contrôles communs sont inclus dans [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] et la bibliothèque est incluse dans [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]. La bibliothèque fournit de nouvelles méthodes qui améliorent les classes existantes et de nouvelles classes et méthodes qui prennent en charge [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] contrôles communs. Lorsque vous créez votre application, vous devez respecter les exigences de compilation et de migration décrites dans les sections suivantes.  
  
## <a name="compilation-requirements"></a>Spécifications de compilation  
  
### <a name="supported-versions"></a>Versions prises en charge  
 Certaines nouvelles classes et méthodes ne prennent en charge que [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] et ses versions ultérieures, alors que d'autres méthodes prennent également en charge les systèmes d'exploitation antérieurs. Une note dans la section `Requirements` de chaque rubrique de la méthode spécifie si le système d'exploitation requis minimal est [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  
  
 Même si votre ordinateur n’exécute pas [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], vous pouvez générer une application MFC qui s’exécutera sur [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] si vous avez les fichiers d’en-tête MFC version 6.1 sur votre ordinateur. Toutefois, les contrôles communs conçus spécifiquement pour [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] fonctionnent uniquement sur ce système et sont ignorées par les systèmes d’exploitation antérieurs.  
  
### <a name="supported-character-sets"></a>Jeux de caractères pris en charge  
 Les nouveaux contrôles communs Windows ne prennent en charge que le jeu de caractères Unicode, et non le jeu de caractères ANSI. Si vous créez votre application à partir de la ligne de commande, utilisez les deux options du compilateur "define (/D)" suivantes pour spécifier Unicode en tant que jeu de caractères sous-jacent :  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 Si vous générez votre application dans l’environnement de développement intégré (IDE) Visual Studio, spécifiez la **du jeu de caractères Unicode** option de le **du jeu de caractères** propriété dans le **général**  nœud des propriétés du projet.  
  
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

