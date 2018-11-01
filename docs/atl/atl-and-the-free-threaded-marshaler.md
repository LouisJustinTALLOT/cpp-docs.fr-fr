---
title: ATL et le marshaleur libre de threads
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: b9baff9af10cd785554e849854556a9aa3bd7ca4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621843"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL et le marshaleur libre de threads

Page de l’Assistant objet Simple ATL attributs fournit une option qui permet à votre classe d’agréger FTM (FTM).

L’Assistant génère du code pour créer une instance de FTM dans `FinalConstruct` et mise en production de cette instance dans `FinalRelease`. Une macro COM_INTERFACE_ENTRY_AGGREGATE est automatiquement ajoutée au mappage COM pour vous assurer que `QueryInterface` les demandes concernant [IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal) sont gérées par le marshaleur libre.

FTM permet un accès direct aux interfaces sur votre objet à partir de n’importe quel thread dans le même processus, accélère les appels entre cloisonnements. Cette option est destinée aux classes qui utilisent le modèle de thread à la fois.

Lorsque vous utilisez cette option, les classes doivent prendre la responsabilité de la sécurité des threads de leurs données. En outre, les objets qui agrègent FTM et doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent suivre des étapes supplémentaires pour garantir que les interfaces sont correctement marshalées. En général, cela implique de stocker les pointeurs d’interface dans la table d’interface globale (GIT) et le pointeur de la GIT chaque fois qu’il est utilisé. ATL fournit la classe [CComGITPtr](../atl/reference/ccomgitptr-class.md) pour vous aider à utiliser des pointeurs d’interface stockés dans le GIT.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Quand utiliser le tableau Global d’Interface](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Problèmes liés aux threads de serveur in-Process](/windows/desktop/com/in-process-server-threading-issues)

