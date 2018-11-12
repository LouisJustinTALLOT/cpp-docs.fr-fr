---
title: Chemins de recherche utilisés dans les règles
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: 26b02fa76920f0d0ff380dacd5aa76cfe8e92c79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649967"
---
# <a name="search-paths-in-rules"></a>Chemins de recherche utilisés dans les règles

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Notes

Une règle d’inférence s’applique à une dépendance uniquement si les chemins d’accès spécifiés dans la dépendance exactement correspondent les chemins d’accès de la règle d’inférence. Spécifiez le répertoire du dépendant dans *frompath* et répertoire de la cible dans *topath*; sans espaces sont autorisés. Spécifiez qu’un seul chemin d’accès pour chaque extension. Un chemin d’accès sur une extension requiert un chemin d’accès sur l’autre. Pour spécifier le répertoire actif, utilisez un point (.) ou accolades vides ({}). Les macros peuvent représenter *frompath* et *topath*; elles sont appelées pendant le prétraitement.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```
{dbi\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUDBI) $<

{ilstore\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{misc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{misc\}.c{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{msf\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{bsc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{mre\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{namesrvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{src\cvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<
```

## <a name="see-also"></a>Voir aussi

[Définition d’une règle](../build/defining-a-rule.md)