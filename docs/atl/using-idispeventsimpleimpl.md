---
title: Utilisation d’IDispEventSimpleImpl (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34fad264e222d27c82f8c1cf79f59664f2c3f601
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850776"
---
# <a name="using-idispeventsimpleimpl"></a>Utilisation d’IDispEventSimpleImpl
Lorsque vous utilisez `IDispEventSimpleImpl` pour gérer les événements, vous devez :  
  
-   Dérivez votre classe de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).  
  
-   Ajoutez une table de récepteur d’événements à votre classe.  
  
-   Définir [les structures _ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) structures décrivant les événements.  
  
-   Ajouter des entrées à la carte de récepteur événement à l’aide du [macro SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) macro.  
  
-   Implémenter les méthodes qui vous intéresse dans la gestion des.  
  
-   Et désinformation la source d’événements.  
  
## <a name="example"></a>Exemple  
 L’exemple ci-dessous vous montre comment gérer les `DocumentChange` événements déclenchement par de Word **Application** objet. Cet événement est défini en tant que méthode sur le `ApplicationEvents` dispinterface.  
  
 L’exemple est issu le [exemple ATLEventHandling](../visual-cpp-samples.md).  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 L’exemple utilise `#import` pour générer les fichiers d’en-tête requis à partir de la bibliothèque de types de Word. Si vous souhaitez utiliser cet exemple avec d’autres versions de Word, vous devez spécifier le fichier mso dll approprié. Par exemple, Office 2000 fournit mso9.dll et OfficeXP fournit mso.dll. Ce code est simplifié dans stdafx.h :  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 Les seules informations à partir de la bibliothèque de types réellement utilisée dans cet exemple sont le CLSID du mot `Application` objet et l’IID de le `ApplicationEvents` interface. Ces informations sont utilisées uniquement au moment de la compilation.  
  
 Le code suivant s’affiche dans Simple.h. Le code correspondant est indiqué par des commentaires :  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 Le code suivant provient de Simple.cpp :  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des événements](../atl/event-handling-and-atl.md)   
 [ATLEventHandling, exemple](../visual-cpp-samples.md)

