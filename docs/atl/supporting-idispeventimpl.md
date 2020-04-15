---
title: Prise en charge d’IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329321"
---
# <a name="supporting-idispeventimpl"></a>Prise en charge d’IDispEventImpl

La classe de modèle [IDispEventImpl](../atl/reference/idispeventimpl-class.md) peut être utilisée pour fournir un support pour les éviers de point de connexion dans votre classe ATL. Un évier de point de connexion permet à votre classe de gérer les événements tirés à partir d’objets COM externes. Ces éviers de point de connexion sont cartographiés avec une carte d’évier d’événement, fournie par votre classe.

Pour implémenter correctement un évier de point de connexion pour votre classe, les étapes suivantes doivent être complétées :

- Importer les bibliothèques de type pour chaque objet externe

- Déclarer `IDispEventImpl` les interfaces

- Déclarer une carte de l’évier de l’événement

- Aviser et déconseillez les points de connexion

Les étapes impliquées dans la mise en œuvre d’un évier de point de connexion sont toutes accomplies en modifiant seulement le fichier d’en-tête (.h) de votre classe.

## <a name="importing-the-type-libraries"></a>Importation des bibliothèques de type

Pour chaque objet externe dont vous souhaitez gérer les événements, vous devez importer la bibliothèque de type. Cette étape définit les événements qui peuvent être traités et fournit des informations qui sont utilisées lors de la déclaration de la carte de l’évier de l’événement. La [directive #import](../preprocessor/hash-import-directive-cpp.md) peut être utilisée pour y parvenir. Ajoutez les `#import` lignes de directive nécessaires pour chaque interface de répartition que vous prendrez en charge au fichier d’en-tête (.h) de votre classe.

L’exemple suivant importe la bibliothèque type`MSCAL.Calendar.7`d’un serveur COM externe (

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Vous devez avoir `#import` une déclaration distincte pour chaque bibliothèque de type externe que vous prendrez en charge.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Déclarer les interfaces IDispEventImpl

Maintenant que vous avez importé les bibliothèques de type de `IDispEventImpl` chaque interface de répartition, vous devez déclarer des interfaces séparées pour chaque interface de répartition externe. Modifiez la déclaration de `IDispEventImpl` votre classe en ajoutant une déclaration d’interface pour chaque objet externe. Pour plus d’informations sur les paramètres, voir [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Le code suivant déclare deux puits de `DCalendarEvents` point de connexion, pour `CMyCompositCtrl2`l’interface, pour l’objet COM mis en œuvre par classe :

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Déclarer une carte de l’évier d’événements

Pour que les notifications d’événement soient traitées par la fonction appropriée, votre classe doit acheminer chaque événement vers son gestionnaire correct. Ceci est réalisé en déclarant une carte d’évier d’événement.

ATL fournit plusieurs macros, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), et [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), qui rendent cette cartographie plus facile. Le format standard est le suivant :

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

L’exemple suivant déclare une carte de l’évier de l’événement avec deux gestionnaires d’événements :

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

La mise en œuvre est presque terminée. La dernière étape concerne le conseil et l’déconseillé des interfaces externes.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Conseiller et déconseillant les interfaces IDispEventImpl

La dernière étape consiste à mettre en œuvre une méthode qui avisera (ou non) tous les points de connexion aux heures appropriées. Ce conseil doit être fait avant que la communication entre les clients externes et votre objet puisse avoir lieu. Avant que votre objet ne devienne visible, chaque interface de répartition externe supportée par votre objet est interrogée pour les interfaces sortantes. Une connexion est établie et une référence à l’interface sortante est utilisée pour gérer les événements à partir de l’objet. Cette procédure est appelée « conseil ».

Une fois votre objet terminé avec les interfaces externes, les interfaces sortantes doivent être notifiées qu’elles ne sont plus utilisées par votre classe. Ce processus est appelé « sans surveillance ».

En raison de la nature unique des objets COM, cette procédure varie, en détail et en exécution, entre les implémentations. Ces détails sont au-delà de la portée de ce sujet et ne sont pas abordés.

## <a name="see-also"></a>Voir aussi

[Principes fondamentaux des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)
