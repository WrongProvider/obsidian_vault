grok final

pelo ingest pipeline so aceitar os metacharacters em \\\ isso n funciona no debugger.

%{TIMESTAMP_ISO8601:tempo} %{HOSTNAME:host.name} (?&lt;event.module&gt;(KES|WSEE))\\\D(?&lt;event.version&gt;(\\\d{1,2}.){3}\\\d{1,2}) %{GREEDYDATA:message}