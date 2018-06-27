---
title: 'TN020 : ID d’affectation de noms et les Conventions de numérotation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.id
dev_langs:
- C++
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca1e78ab4b94d9055b8f0c7cc14bde12506695b8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951365"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020 : conventions de dénomination d'ID et de numérotation
Cette note décrit les ID d’affectation de noms et les conventions de numérotation MFC 2.0 utilise pour les ressources, les commandes, les chaînes, les contrôles et fenêtres enfants.  
  
 La dénomination d’ID de MFC et conventions de numérotation sont conçus pour remplir les conditions suivantes :  
  
-   Fournir une norme d’affectation de noms ID cohérente utilisée dans la bibliothèque MFC et les applications MFC qui sont pris en charge par l’éditeur de ressources Visual C++. Cela facilite le programmeur interpréter le type et l’origine d’une ressource à partir de son ID.  
  
-   Mettre en évidence la relation 1-à-1 fort entre certains types de codes.  
  
-   Être conforme aux normes déjà largement utilisées pour nommer les ID dans Windows.  
  
-   L’espace de numérotation des ID de partition. Numéros d’identification peuvent être affectés par le programmeur, MFC, Windows et modifiées de Visual C++ de ressources. Partitionnement appropriées aidera à éviter la duplication de numéros d’identification.  
  
## <a name="the-id-prefix-naming-convention"></a>La Convention d’affectation de noms du préfixe d’identificateur  
 Plusieurs types de codes peuvent se produire dans une application. La convention de dénomination d’ID de MFC définit des préfixes différents pour différents types de ressources.  
  
 MFC utilise le préfixe « IDR_ » pour indiquer un ID de ressource qui s’applique à plusieurs types de ressource. Par exemple, pour une fenêtre frame donné, MFC utilise le même préfixe « IDR_ » pour indiquer une ressource de menu, accélérateur, chaîne et l’icône. Le tableau suivant présente les différents préfixes et leur utilisation :  
  
|Préfixe|Utilisez|  
|------------|---------|  
|IDR_|Pour plusieurs types de ressources (utilisés principalement pour les menus, des accélérateurs et rubans).|  
|IDD_|Pour les ressources de modèle de boîte de dialogue (par exemple, IDD_DIALOG1).|  
|IDC_|Pour les ressources de curseur.|  
|IDI_|Pour les ressources de l’icône.|  
|IDB_|Pour les ressources de l’image bitmap.|  
|IDS_|Pour les ressources de chaîne.|  
  
 Au sein d’une ressource de boîte de dialogue MFC suit les conventions suivantes :  
  
|Préfixe ou une étiquette|Utilisez|  
|---------------------|---------|  
|IDOK, IDCANCEL|Pour le bouton de commande ID standard.|  
|IDC_|Pour d’autres contrôles de boîte de dialogue.|  
  
 Le préfixe « IDC_ » est également utilisé pour les curseurs. Ce conflit d’affectation de noms n’est pas généralement un problème, car une application classique aura peu de curseurs et de nombreux contrôles de boîte de dialogue.  
  
 Au sein d’une ressource de menu, MFC suit les conventions suivantes :  
  
|Préfixe|Utilisez|  
|------------|---------|  
|IDM_|Pour les éléments de menu qui n’utilisent pas l’architecture de commande MFC.|  
|ID_|Pour les commandes de menu qui utilisent l’architecture de commande MFC.|  
  
 Les commandes qui suivent l’architecture de la commande MFC doivent posséder un gestionnaire de commandes ON_COMMAND et peuvent avoir un gestionnaire ON_UPDATE_COMMAND_UI. Si ces gestionnaires de commandes suivent l’architecture de commande MFC, elles fonctionneront correctement si elles sont liées à une commande de menu, un bouton de barre d’outils ou un bouton de barre de boîte de dialogue. Le même préfixe « ID_ » est également utilisé pour une chaîne d’invite de menu qui s’affiche sur la barre de message du programme. La plupart des éléments de menu dans votre application doit suivre les conventions de commande MFC. Tous les ID de commande standard (par exemple, ID_FILE_NEW) suivent cette convention.  
  
 MFC utilise également « IDP_ » comme une forme spécialisée de chaînes (au lieu de « service »). Les chaînes avec le préfixe « IDP_ » sont des invites, autrement dit, les chaînes utilisées dans les boîtes de message. Les chaînes « IDP_ » peuvent contenir « %1 » et « %2 » en tant qu’espaces réservés de chaînes déterminés par le programme. Les chaînes « IDP_ » ont généralement les rubriques d’aide associées, et non les chaînes « Service ». Les chaînes « IDP_ » sont toujours localisés, et les chaînes « Service » ne peuvent pas être localisées.  
  
 La bibliothèque MFC utilise également le préfixe « IDW_ » comme une forme spécialisée d’ID (au lieu de « IDC_ »). Ces ID est attribuées aux fenêtres enfants tels que les vues et fenêtres fractionnées par les classes du framework. ID d’implémentation MFC sont précédés de « AFX_ ».  
  
## <a name="the-id-numbering-convention"></a>La Convention de numérotation des ID  
 Le tableau suivant répertorie les plages valides pour les ID des types spécifiques. Certaines limites sont des limites de l’implémentation technique, et d’autres conventions sont conçues pour empêcher que votre ID en conflit avec les ID prédéfinis de Windows ou MFC, les implémentations par défaut.  
  
 Nous recommandons vivement que vous définissez tous les ID dans les plages recommandées. La limite inférieure de ces plages est 1, car 0 n’est pas utilisé. Nous recommandons que vous utilisez la convention commune et 100 ou 101 en tant que le premier ID.  
  
|Préfixe|Type de ressource|Plage valide|  
|------------|-------------------|-----------------|  
|IDR_|multiples|entre 1 et 0x6FFF|  
|IDD_|modèles de boîte de dialogue|entre 1 et 0x6FFF|  
|IDC_, IDI_, IDB_|curseurs, les icônes, les bitmaps|entre 1 et 0x6FFF|  
|SERVICE, IDP_|chaînes générales|entre 1 et 0x7FFF|  
|ID_|commandes|0 x 8000 et 0xDFFF|  
|IDC_|contrôles|8 et 0xDFFF|  
  
 Raisons de ces limites de plage suivantes :  
  
-   Par convention, la valeur d’ID de 0 n’est pas utilisée.  
  
-   Limitations de mise en œuvre Windows restreindre true ID de ressource à être inférieure ou égale à 0x7FFF.  
  
-   Structure interne de MFC réserve ces plages :  
  
    -   0x7000 via 0x7FFF (voir afxres.h)  
  
    -   0xE000 via 0xEFFF (voir afxres.h)  
  
    -   16000 via 18000 (voir afxribbonres.h)  
  
     Ces plages peuvent changer dans les futures mises en œuvre de MFC.  
  
-   Plusieurs commandes du système Windows utilisent la plage de 0xF000 à 0xFFFF.  
  
-   ID de contrôle de 1 à 7 sont réservés pour les contrôles standard tels que IDOK et IDCANCEL.  
  
-   La plage de 0 x 8000 et 0xFFFF pour les chaînes est réservée aux invites de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

