---
description: 'En savoir plus sur : écriture de vos propres manipulateurs sans arguments'
title: Écrire vos propres manipulateurs sans arguments
ms.date: 11/04/2016
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
ms.openlocfilehash: 593db0a3dacb54c94cc865ebc20b1e1b39d2c208
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187752"
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Écrire vos propres manipulateurs sans arguments

Écrire des manipulateurs qui n’utilisent pas d’arguments ne requiert ni dérivation de classe, ni utilisation de macros complexes. Supposons que votre imprimante requiert la paire \<ESC> [pour passer en mode gras. Vous pouvez insérer cette paire directement dans le flux :

```cpp
cout << "regular " << '\033' << '[' << "boldface" << endl;
```

Ou vous pouvez définir le manipulateur `bold`, qui insère les caractères :

```cpp
ostream& bold(ostream& os) {
    return os << '\033' << '[';
}
cout << "regular " << bold << "boldface" << endl;
```

La fonction `bold` définie globalement accepte un argument de référence `ostream` et retourne la référence `ostream`. Ce n’est pas une fonction membre ou amie, car elle n’a besoin d’accéder à aucun élément de classe privée. La fonction `bold` se connecte au flux car l’opérateur `<<` du flux est surchargé pour accepter ce type de fonction, utilisant une déclaration qui ressemble quelque peu à ceci :

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{
    // call ios_base manipulator
    (*_Pfn)(*(ios_base *)this);

    return (*this);
}
```

Vous pouvez utiliser cette fonctionnalité pour étendre d’autres opérateurs surchargés. Dans ce cas, il est accessoire que `bold` insère des caractères dans le flux. La fonction est appelée lorsqu’elle est insérée dans le flux, mais pas nécessairement lorsque les caractères adjacents sont imprimés. Par conséquent, l’impression peut être retardée en raison de la mise en mémoire tampon du flux.

## <a name="see-also"></a>Voir aussi

[Flux de sortie](../standard-library/output-streams.md)
