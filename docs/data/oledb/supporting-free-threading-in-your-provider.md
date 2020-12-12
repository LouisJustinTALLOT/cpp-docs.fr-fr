---
description: 'En savoir plus sur : prise en charge des threads libres dans votre fournisseur'
title: Prise en charge du Free Threading dans votre fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 4f6785dd85ae043ce0ee74c1dda4fa365c566729
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286473"
---
# <a name="supporting-free-threading-in-your-provider"></a>Prise en charge du Free Threading dans votre fournisseur

Toutes les classes de fournisseur OLE DB sont thread-safe, et les entrées de Registre sont définies en conséquence. Il est judicieux de prendre en charge le Threading gratuit pour fournir un niveau élevé de performances dans les situations multi-utilisateur. Pour garantir la sécurité des threads de votre fournisseur, vous devez vérifier que votre code est bloqué correctement. Chaque fois que vous écrivez ou stockez des données, vous devez bloquer l’accès avec les sections critiques.

Chaque objet de modèle de fournisseur OLE DB possède sa propre section critique. Pour faciliter le blocage, chaque nouvelle classe que vous créez doit être une classe de modèle acceptant le nom de la classe parente comme argument.

L’exemple suivant montre comment bloquer votre code :

```cpp
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

Pour plus d’informations sur la façon de protéger des sections critiques avec `Lock` et `Unlock` , consultez [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Vérifiez que toutes les méthodes que vous substituez (comme `Execute` ) sont thread-safe.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
