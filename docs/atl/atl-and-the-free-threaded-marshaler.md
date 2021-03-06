---
description: 'En savoir plus sur : ATL et le marshaleur libre de threads'
title: ATL et le marshaleur libre de threads
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: 01fb54386b5f48c8e49cc805e047c0faf8b0c39b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166068"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL et le marshaleur libre de threads

La page attributs de l’Assistant objet simple ATL fournit une option qui permet à votre classe d’agréger le marshaleur libre de threads (FTM).

L’Assistant génère du code pour créer une instance du marshaleur libre de threads dans `FinalConstruct` et libérer cette instance dans `FinalRelease` . Une macro COM_INTERFACE_ENTRY_AGGREGATE est automatiquement ajoutée au mappage COM pour s’assurer que `QueryInterface` les demandes de [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) sont gérées par le marshaleur libre de threads.

Le marshaleur libre de threads autorise l’accès direct aux interfaces de votre objet depuis n’importe quel thread du même processus, accélérant ainsi les appels inter-cloisonnements. Cette option est destinée aux classes qui utilisent le modèle de thread.

Quand vous utilisez cette option, les classes doivent assumer la responsabilité de la sécurité des threads de leurs données. En outre, les objets qui agrègent le marshaleur de thread libre et doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent effectuer des étapes supplémentaires pour garantir que les interfaces sont correctement marshalées. En général, cela implique le stockage des pointeurs d’interface dans la table GIT (Global Interface Table) et l’obtention du pointeur de la table GIT chaque fois qu’elle est utilisée. ATL fournit la classe [CComGITPtr](../atl/reference/ccomgitptr-class.md) pour vous aider à utiliser des pointeurs d’interface stockés dans le git.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Quand utiliser la table d’interface globale](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Problèmes liés aux threads du serveur in-process](/windows/win32/com/in-process-server-threading-issues)
