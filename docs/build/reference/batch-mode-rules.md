---
title: Règles en mode batch
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328412"
---
# <a name="batch-mode-rules"></a>Règles en mode batch

```
{frompath}.fromext{topath}.toext::
   commands
```

Les règles d’inférence en mode par lots ne fournissent qu’une seule invocation de la règle d’inférence lorsque les commandes N passent par cette règle d’inférence. Sans règles d’inférence en mode par lots, il faudrait invoquer les commandes N. N est le nombre de personnes à charge qui déclenchent la règle de l’inférence.

Lesfils qui contiennent des règles d’inférence en mode par lots doivent utiliser la version NMAKE 1.62 ou plus. Pour vérifier la version NMAKE, exécutez la macro _NMAKE_VER disponible avec la version NMAKE 1.62 ou plus. Cette macro renvoie une chaîne représentant la version produit Visual C.

La seule différence syntaxique par rapport à la règle d’inférence standard est que la règle d’inférence en mode par lots est terminée avec un double côlon (::).

> [!NOTE]
> L’outil invoqué doit être en mesure de traiter plusieurs fichiers. La règle d’inférence `$<` en mode par lots doit être utilisée comme macro pour accéder aux fichiers dépendants.

Les règles d’inférence en mode par lots peuvent accélérer le processus de construction. Il est plus rapide de fournir des fichiers au compilateur en lots, parce que le pilote compilateur n’est invoqué qu’une seule fois. Par exemple, le compilateur C et CMD fonctionne mieux lors du traitement d’un ensemble de fichiers parce qu’il peut rester résident de la mémoire pendant le processus.

L’exemple suivant montre comment utiliser les règles d’inférence en mode par lots :

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

NMAKE produit la sortie suivante sans règles d’inférence en mode par lots :

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

NMAKE produit le résultat suivant avec les règles d’inférence en mode par lots :

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

[Règles d'inférence](inference-rules.md)
