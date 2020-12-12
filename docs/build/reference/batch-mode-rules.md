---
description: En savoir plus sur les règles de Batch-Mode
title: Règles en mode batch
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 73439082b4e2ad8e33b104329d861ddd1919ec63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182734"
---
# <a name="batch-mode-rules"></a>Règles en mode batch

```
{frompath}.fromext{topath}.toext::
   commands
```

Les règles d’inférence en mode batch ne fournissent qu’un seul appel de la règle d’inférence lorsque N commandes passent par cette règle d’inférence. Sans règles d’inférence en mode batch, il faut appeler N commandes. N est le nombre de dépendants qui déclenchent la règle d’inférence.

Les Makefiles qui contiennent des règles d’inférence en mode batch doivent utiliser NMAKE version 1,62 ou ultérieure. Pour vérifier la version NMAKE, exécutez la macro _NMAKE_VER disponible avec NMAKE version 1,62 ou ultérieure. Cette macro retourne une chaîne représentant le Visual C++ version du produit.

La seule différence syntaxique par rapport à la règle d’inférence standard est que la règle d’inférence en mode traitement par lot se termine par un double deux-points ( ::).

> [!NOTE]
> L’outil appelé doit pouvoir gérer plusieurs fichiers. La règle d’inférence en mode batch doit utiliser `$<` comme macro pour accéder aux fichiers dépendants.

Les règles d’inférence en mode batch peuvent accélérer le processus de génération. Il est plus rapide de fournir des fichiers au compilateur par lots, car le pilote du compilateur est appelé une seule fois. Par exemple, le compilateur C et C++ s’exécute mieux lors de la gestion d’un ensemble de fichiers, car il peut rester résident dans la mémoire pendant le processus.

L’exemple suivant montre comment utiliser des règles d’inférence en mode batch :

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE produit la sortie suivante sans règles d’inférence en mode batch :

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE produit le résultat suivant avec les règles d’inférence en mode batch :

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
