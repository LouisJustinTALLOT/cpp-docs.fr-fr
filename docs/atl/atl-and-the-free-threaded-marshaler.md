---
title: ATL et le marshaleur libre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 015b07e5870aa6269dc76af8610d42fb469a6d33
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848348"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL et le marshaleur libre de threads
Page de l’Assistant objet Simple ATL attributs fournit une option qui permet à votre classe d’agréger FTM (FTM).  
  
 L’Assistant génère du code pour créer une instance de FTM dans `FinalConstruct` et mise en production de cette instance dans `FinalRelease`. Une macro COM_INTERFACE_ENTRY_AGGREGATE est automatiquement ajoutée au mappage COM pour vous assurer que `QueryInterface` les demandes concernant [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) sont gérées par le marshaleur libre.  
  
 FTM permet un accès direct aux interfaces sur votre objet à partir de n’importe quel thread dans le même processus, accélère les appels entre cloisonnements. Cette option est destinée aux classes qui utilisent le modèle de thread à la fois.  
  
 Lorsque vous utilisez cette option, les classes doivent prendre la responsabilité de la sécurité des threads de leurs données. En outre, les objets qui agrègent FTM et doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent suivre des étapes supplémentaires pour garantir que les interfaces sont correctement marshalées. En général, cela implique de stocker les pointeurs d’interface dans la table d’interface globale (GIT) et le pointeur de la GIT chaque fois qu’il est utilisé. ATL fournit la classe [CComGITPtr](../atl/reference/ccomgitptr-class.md) pour vous aider à utiliser des pointeurs d’interface stockés dans le GIT.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [Quand utiliser le tableau Global d’Interface](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Problèmes liés aux threads de serveur in-Process](http://msdn.microsoft.com/library/windows/desktop/ms687205)

