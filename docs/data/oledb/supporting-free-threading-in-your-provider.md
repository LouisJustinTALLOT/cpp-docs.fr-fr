---
title: Prise en charge du Free Threading dans votre fournisseur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9c61aea0fec1f6d808a0a34ee74bd0ce2d399a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108512"
---
# <a name="supporting-free-threading-in-your-provider"></a>Prise en charge du Free Threading dans votre fournisseur
Toutes les classes du fournisseur OLE DB sont thread-safe, et les entrées de Registre sont définies en conséquence. Il est judicieux de prendre en charge le modèle de thread libre afin de fournir un niveau élevé de performances dans les situations multi-utilisateur. Pour aider à conserver un fournisseur thread-safe, vous devez vérifier que votre code est bloqué correctement. Chaque fois que vous écrivez ou stockez des données, vous devez bloquer l’accès à des sections critiques.  
  
 Chaque objet de modèle de fournisseur OLE DB possède sa propre section critique. Pour faciliter le blocage, chaque nouvelle classe que vous créez doit être une classe de modèle prend la classe parente nom en tant qu’argument.  
  
 L’exemple suivant montre comment bloquer le code :  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 Pour plus d’informations sur la façon de protéger les sections critiques avec `Lock` et `Unlock`, consultez [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
 Vous devez également vérifier que toutes les méthodes que vous substituez (tel que `Execute`) sont thread-safe.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)