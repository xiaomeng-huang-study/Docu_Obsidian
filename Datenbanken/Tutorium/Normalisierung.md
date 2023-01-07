| Matrikel_Nr. | Vorname_Student | Nachname_Student | Adresse_Student |
| ------------ | --------------- | ---------------- | --------------- |
|              |                 |                  |                 |

| Hochschul_Nr. | Name_HS | Adresse_HS | Rektor_Nr | Vorname_Rektor | Nachname_Rektor    |
| ------------- | ------- | ---------- | --------- | -------------- | --- |
|               |         |            |           |                |     |

| Matrikel_Nr. | Hochschul_Nr. | Bewertung    |
|:------------ |:------------- |:--- |
|              |               |     |

3.Normalform
Student:
| Matrikel_Nr. | Vorname_Student | Nachname_Student | Adresse_Student |
| ------------ | --------------- | ---------------- | --------------- |
|              |                 |                  |                 |

Hochschule:
| Hochschul_Nr. | Name_HS | Adresse_HS | Rektor_Nr    |
|:------------- |:------- |:---------- |:--- |
|               |         |            |     |

Rektor:
| Rektor_Nr. | Vorname_Rektor | Nachname_Rektor    |
|:---------- |:-------------- |:--- |
|            |                |     |

Bewertung:
| Matrikel_Nr. | Hochschul_Nr. | Bewertung    |
|:------------ |:------------- |:--- |
|              |               |     |

