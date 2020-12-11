---
description: 'En savoir plus sur : IDispEventImpl de prise en charge'
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
ms.openlocfilehash: 6a5c12e011ad0dc0f27594325a22dadddd5b92c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157371"
---
# <a name="supporting-idispeventimpl"></a>Prise en charge d’IDispEventImpl

La classe de modèle [IDispEventImpl](../atl/reference/idispeventimpl-class.md) peut être utilisée pour assurer la prise en charge des récepteurs de points de connexion dans votre classe ATL. Un récepteur de points de connexion permet à votre classe de gérer des événements déclenchés à partir d’objets COM externes. Ces récepteurs de points de connexion sont mappés à une table de récepteurs d’événements, fournie par votre classe.

Pour implémenter correctement un récepteur de point de connexion pour votre classe, vous devez effectuer les étapes suivantes :

- Importer les bibliothèques de types pour chaque objet externe

- Déclarer les `IDispEventImpl` interfaces

- Déclarer une table de récepteurs d’événements

- Conseillez et Déconseillez les points de connexion

Les étapes nécessaires à l’implémentation d’un récepteur de point de connexion sont toutes effectuées en modifiant uniquement le fichier d’en-tête (. h) de votre classe.

## <a name="importing-the-type-libraries"></a>Importation des bibliothèques de types

Pour chaque objet externe dont vous souhaitez gérer les événements, vous devez importer la bibliothèque de types. Cette étape définit les événements qui peuvent être gérés et fournit des informations qui sont utilisées lors de la déclaration du mappage de récepteur d’événements. Pour ce faire, vous pouvez utiliser la directive [#import](../preprocessor/hash-import-directive-cpp.md) . Ajoutez les `#import` lignes de directive nécessaires pour chaque interface de dispatch que vous prendrez en charge dans le fichier d’en-tête (. h) de votre classe.

L’exemple suivant importe la bibliothèque de types d’un serveur COM externe ( `MSCAL.Calendar.7` ) :

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Vous devez disposer d’une `#import` instruction distincte pour chaque bibliothèque de types externe que vous allez prendre en charge.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Déclaration des interfaces IDispEventImpl

Maintenant que vous avez importé les bibliothèques de types de chaque interface de dispatch, vous devez déclarer `IDispEventImpl` des interfaces distinctes pour chaque interface de dispatch externe. Modifiez la déclaration de votre classe en ajoutant une `IDispEventImpl` déclaration d’interface pour chaque objet externe. Pour plus d’informations sur les paramètres, consultez [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Le code suivant déclare deux récepteurs de points de connexion pour l' `DCalendarEvents` interface pour l’objet com implémenté par la classe `CMyCompositCtrl2` :

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Déclaration d’une table de récepteurs d’événements

Pour que les notifications d’événements soient gérées par la fonction appropriée, votre classe doit acheminer chaque événement vers son gestionnaire correct. Pour ce faire, il faut déclarer une table de récepteurs d’événements.

ATL fournit plusieurs macros, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)et [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)qui facilitent ce mappage. Le format standard est le suivant :

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

L’exemple suivant déclare une table de récepteurs d’événements avec deux gestionnaires d’événements :

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

L’implémentation est presque terminée. La dernière étape concerne le Conseil et le désavertissement des interfaces externes.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Avertissement et désavertissement des interfaces IDispEventImpl

La dernière étape consiste à implémenter une méthode qui conseille (ou déconseiller) tous les points de connexion aux moments appropriés. Cet avertissement doit être effectué avant que la communication entre les clients externes et votre objet puisse avoir lieu. Avant que votre objet ne devienne visible, chaque interface de dispatch externe prise en charge par votre objet est interrogée pour les interfaces sortantes. Une connexion est établie et une référence à l’interface sortante est utilisée pour gérer les événements de l’objet. Cette procédure est appelée « avertissement ».

Une fois votre objet terminé avec les interfaces externes, les interfaces sortantes doivent être informées qu’elles ne sont plus utilisées par votre classe. Ce processus est appelé « désavertissement ».

En raison de la nature unique des objets COM, cette procédure varie, en détail et en cours d’exécution, entre les implémentations. Ces détails n’entrent pas dans le cadre de cette rubrique et ne sont pas traités.

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)
