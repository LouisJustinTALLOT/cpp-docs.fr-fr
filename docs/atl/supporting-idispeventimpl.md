---
title: Prise en charge de IDispEventImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 680396ae912cca5f19e87697e7de0033213cc963
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362217"
---
# <a name="supporting-idispeventimpl"></a>Prise en charge de IDispEventImpl
La classe de modèle [IDispEventImpl](../atl/reference/idispeventimpl-class.md) peut être utilisé pour prendre en charge des récepteurs de point de connexion dans votre classe ATL. Un récepteur de points de connexion permet à votre classe gérer les événements déclenchés à partir des objets COM externes. Ces récepteurs de points de connexion sont mappés avec une table de récepteur d’événements, fournie par votre classe.  
  
 Pour implémenter correctement un récepteur de points de connexion pour votre classe, vous devant effectuer les étapes suivantes :  
  
-   Importer des bibliothèques de types pour chaque objet externe  
  
-   Déclarez le `IDispEventImpl` interfaces  
  
-   Déclarer une table de récepteur d’événements  
  
-   Notifications et de déconseiller les points de connexion  
  
 Les étapes de l’implémentation d’un récepteur de point de connexion sont effectuées en modifiant uniquement le fichier d’en-tête (.h) de votre classe.  
  
## <a name="importing-the-type-libraries"></a>L’importation de bibliothèques de types  
 Pour chaque objet externe dont vous souhaitez gérer les événements, vous devez importer la bibliothèque de types. Cette étape définit les événements qui peuvent être gérés et fournit des informations qui sont utilisées lors de la déclaration de la table de récepteur d’événements. Le [#import](../preprocessor/hash-import-directive-cpp.md) directive peut être utilisée pour y parvenir. Ajouter nécessaires `#import` lignes la directive pour chaque interface de dispatch que vous prendrez en charge pour le fichier d’en-tête (.h) de votre classe.  
  
 L’exemple suivant importe la bibliothèque de types d’un serveur COM externe (`MSCAL.Calendar.7`) :  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  Vous devez définir un `#import` instruction pour chaque bibliothèque de types externes prendra en charge.  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>Déclarer des Interfaces IDispEventImpl  
 Maintenant que vous avez importé les bibliothèques de types de chaque interface de dispatch, vous devez déclarer distinct `IDispEventImpl` des interfaces pour chaque interface de dispatch externe. Modifiez la déclaration de votre classe en ajoutant une `IDispEventImpl` déclaration pour chaque objet externe de l’interface. Pour plus d’informations sur les paramètres, consultez [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
 Le code suivant déclare deux récepteurs de points de connexion pour le `DCalendarEvents` interface, pour l’objet COM implémentée par la classe `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>Déclaration d’une table de récepteur d’événements  
 Dans l’ordre pour les notifications d’événements à être gérées par la fonction, votre classe doit acheminer chaque événement à son gestionnaire correspondant. Cela est possible en déclarant une table de récepteur d’événements.  
  
 ATL fournit plusieurs macros, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), et [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), qui rendent ce mappage plus facile. Le format standard est la suivante :  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 L’exemple suivant déclare une table de récepteur d’événements avec deux gestionnaires d’événements :  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 L’implémentation est presque terminée. La dernière étape concerne informer et annulation des interfaces externes.  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Information et désinformation des Interfaces IDispEventImpl  
 L’étape finale consiste à implémenter une méthode qui sera Conseiller (ou déconseiller) tous les points de connexion aux moments opportuns. Cette information doit être effectuée avant que la communication entre les clients externes et votre objet peut avoir lieu. Avant que vos objets deviennent visibles, chaque interface de dispatch externe prise en charge par votre objet est interrogée pour les interfaces sortantes. Une connexion est établie et une référence à l’interface sortante est utilisée pour gérer les événements de l’objet. Cette procédure est appelée « conseiller ».  
  
 Une fois votre objet est terminé avec les interfaces externes, les interfaces sortantes doivent être informés qu’ils ne sont plus utilisés par votre classe. Ce processus est appelé « désinformation ».  
  
 En raison de la nature unique des objets COM, la procédure varie en détail et de l’exécution, entre les implémentations. Ces détails sortent du cadre de cette rubrique et ne sont pas traitées.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)

