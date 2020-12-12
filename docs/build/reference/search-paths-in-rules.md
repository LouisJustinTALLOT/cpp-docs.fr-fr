---
description: En savoir plus sur les chemins de recherche dans les règles
title: Chemins de recherche utilisés dans les règles
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: bf070fc57907b68eb458b8a5276698282ef30f9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224879"
---
# <a name="search-paths-in-rules"></a>Chemins de recherche utilisés dans les règles

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Notes

Une règle d’inférence s’applique à une dépendance uniquement si les chemins d’accès spécifiés dans la dépendance correspondent exactement aux chemins d’accès des règles d’inférence. Spécifiez le répertoire du dépendant dans *fromPath* et le répertoire de la cible dans *toPath*; aucun espace n’est autorisé. Spécifiez un seul chemin d’accès pour chaque extension. Un chemin d’accès sur une extension requiert un chemin d’accès sur l’autre. Pour spécifier le répertoire actif, utilisez un point (.) ou des accolades vides ({}). Les macros peuvent représenter *fromPath* et *toPath*; elles sont appelées pendant le prétraitement.

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
