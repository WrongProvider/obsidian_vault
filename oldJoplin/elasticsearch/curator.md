curator

- filtertype: pattern
	kind: regex
    value: '^(alpha-|bravo-|charlie-).*$'
	
	ou
	
	kind: prefix
    value: logstash-
	se colocar "exclude: True" será usado todos os indices exceto o logstash.