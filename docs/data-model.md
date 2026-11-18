# Data model

## Casos

One record per validated context. Each record corresponds to an alert family that was reviewed with the client.

| Field | Type | Description | Rule |
|---|---|---|---|
| Title | Single line of text | Alert name as the tool reports it | Use the exact name, so it is easy to search |
| TituloContexto | Single line of text | Short descriptive title of the context | Start with the business context, not the alert |
| Incidente | Single line of text | Ticket number | Format `SOC-` + number. Leave empty if unknown |
| TacticaMITRE | Choice | MITRE ATT&CK tactic | Taken from the tool when it reports one, otherwise proposed and reviewed |
| Tecnologia | Choice | Source tool | Values from the Listas sheet |
| Categoria | Choice | Type of entity involved | Values from the Listas sheet |
| Contexto | Multiple lines of text | What was validated and how | Facts only, no recommendation |
| Considerar | Multiple lines of text | What the analyst should do | Starts with "Considerar actividad legítima cuando..." or similar |
| Vigencia | Date only | Last day the context applies | Required. See validity rules |
| Revision | Choice | Review status | OK or Renovar |
| Responsable | Person or text | Who maintains the record | Team or named owner |
| FechaReporte | Date only | Date the context was reported | Required |
| Semana | Single line of text | Week label | For grouping in views |
| CuentaUsuario | Single line of text | Account or user involved | Use placeholders in shared copies |
| EquipoHost | Single line of text | Host or resource involved | Use placeholders in shared copies |

### Validity rules

- A context is **valid** until its Vigencia date. Standard duration is one week, from Monday to Sunday, unless the case requires a different window (for example, a trip or a temporary exception).
- When a context expires, keep the record as history. Do not delete it.
- Renew a context by creating a new record with a new Vigencia date, or by updating Revision to Renovar when the same context needs review.

### Status chips

| Status | Condition |
|---|---|
| Vigente | Vigencia is more than 30 days away |
| Por vencer | Vigencia is within 30 days |
| Vencida | Vigencia has passed |
| Sin vigencia | Vigencia is empty |

## IOCs

| Field | Type | Description |
|---|---|---|
| ID | Single line of text | Sequential ID, for example `IOC-001` |
| Tipo | Choice | IP, Dominio, URL, Hash SHA256 or Correo |
| Indicador | Single line of text | The indicator value |
| Estado | Choice | Bloqueado, En progreso or Desbloqueado |
| Severidad | Choice | Baja, Media, Alta or Crítica |
| Incidente | Single line of text | Related ticket |
| FechaReporte | Date only | Date the indicator was reported |
| Comentario | Multiple lines of text | Short note |

Store only the indicator itself, not the investigation details. The details stay in the ticket.

## Listas

Reference values for choice columns. Keep the values exactly as written; any change must be made in the list settings and in this file at the same time.

## Naming conventions

- Lists: `Casos`, `IOCs`, `Listas`.
- Internal column names: no spaces, no accents, no special characters.
- Incident IDs: `SOC-` followed by the number, with no extra characters.
