---
description: 'En savoir plus sur : pragma init_seg'
title: init_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: cab1c82acd3e06a0ace4d55be3ce82e8fd7aed1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236462"
---
# <a name="init_seg-pragma"></a>init_seg, pragma

**Section spécifique à C++**

Spécifie un mot clé ou une section de code qui affecte l'ordre dans lequel le code de démarrage est exécuté.

## <a name="syntax"></a>Syntaxe

> **#pragma init_seg (** {, utilisateur de la bibliothèque de **compilateurs**  |    |   | "*section-Name*" [ **,** *Func-Name* ]} **)**

## <a name="remarks"></a>Notes

Les termes « *segment* » et « *section »* ont la même signification dans cet article.

Étant donné que le code est parfois requis pour initialiser des objets statiques globaux, vous devez spécifier quand créer les objets. En particulier, il est important d’utiliser le pragma **init_seg** dans les bibliothèques de liens dynamiques (dll), ou dans les bibliothèques qui requièrent une initialisation.

Les options du pragma **init_seg** sont les suivantes :

**compiler**\
Réservé pour l'initialisation de la bibliothèque Runtime C Microsoft. Les objets de ce groupe sont construits en premier.

**lib**\
Disponible pour les initialisations des fournisseurs de bibliothèques de classes tierces. Les objets de ce groupe sont construits après ceux marqués comme **compilateur**, mais avant les autres.

**utilisateur**\
Disponible pour tout utilisateur. Les objets de ce groupe sont construits en dernier.

*nom de la section*\
Autorise la spécification explicite de la section d'initialisation. Les objets d’un nom de *section* spécifié par l’utilisateur ne sont pas implicitement construits. Toutefois, leurs adresses sont placées dans la section nommée par *section-Name*.

La *section-Name* que vous donnez contient des pointeurs vers des fonctions d’assistance qui créeront les objets globaux déclarés après le pragma dans ce module.

Pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section, consultez [/section](../build/reference/section-specify-section-attributes.md).

*Func-Name*\
Spécifie une fonction à appeler au lieu de `atexit` lorsque le programme se ferme. Cette fonction d’assistance appelle également [atexit](../c-runtime-library/reference/atexit.md) avec un pointeur vers le destructeur de l’objet global. Si vous spécifiez un identificateur de fonction dans le pragma du formulaire,

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

votre fonctionnalité est appelée à la place de l'`atexit`de la bibliothèque Runtime C. Elle vous permet de générer une liste des destructeurs à appeler lorsque vous êtes prêt à détruire les objets.

Si vous devez différer l'initialisation (par exemple, dans une DLL) vous pouvez choisir de spécifier le nom de section explicitement. Votre code doit ensuite appeler les constructeurs pour chaque objet statique.

Il ne reste aucun guillemet autour de l'identificateur du remplacement d'`atexit`.

Vos objets seront toujours placés dans les sections définies par les autres `XXX_seg` pragmas.

Les objets déclarés dans le module ne sont pas automatiquement initialisés par le runtime C. Votre code doit effectuer l’initialisation.

Par défaut, les sections `init_seg` sont en lecture seule. Si le nom de la section est `.CRT` , le compilateur change l’attribut en mode lecture seule, même s’il est marqué comme étant en lecture et en écriture.

Vous ne pouvez pas spécifier **init_seg** plusieurs fois dans une unité de traduction.

Même si votre objet n’a pas de constructeur défini par l’utilisateur, un défini explicitement dans le code, le compilateur peut en générer un pour vous. Par exemple, il peut en créer un pour lier les pointeurs v-table. Le cas échéant, votre code appelle le constructeur généré par le compilateur.

## <a name="example"></a>Exemple

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
