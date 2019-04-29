---
title: Chemins de recherche utilisés dans les règles
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: eab6e9d32940aaf5729ce82c4e8258a3a3132208
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318860"
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

[Définition d’une règle](defining-a-rule.md)
