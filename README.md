# Google-Dorking-and-OSINT
# Configuration files
        site:target.com ext:xml | ext:conf | ext:cfg | ext:ini | ext:env | ext:yml | ext:yaml | ext:toml
        site:target.com filetype:env
        site:target.com filetype:yml "password"

# Database files
       site:target.com ext:sql | ext:db | ext:sqlite | ext:mdb
       site:target.com filetype:sql "INSERT INTO"
       site:target.com filetype:sql "CREATE TABLE"

# Backup files
       site:target.com ext:bak | ext:backup | ext:old | ext:temp | ext:swp | ext:save
       site:target.com filetype:zip | filetype:tar | filetype:gz | filetype:rar
       site:target.com inurl:backup

# Log files
       site:target.com ext:log
       site:target.com filetype:log "error" | "warning" | "fatal"
       site:target.com filetype:log "password" | "user"

# Source code
       site:target.com ext:php | ext:asp | ext:aspx | ext:py | ext:rb | ext:java
       site:target.com ext:git
       site:target.com inurl:.git

# Credentials and secrets
      site:target.com "password" | "passwd" | "pwd" filetype:txt
      site:target.com "api_key" | "apikey" | "api-key" | "secret_key"
      site:target.com "aws_access_key_id" | "aws_secret_access_key"
      site:target.com "BEGIN RSA PRIVATE KEY" | "BEGIN OPENSSH PRIVATE KEY"
      site:target.com "jdbc:" | "mongodb://" | "mysql://" | "postgresql://"
      site:target.com filetype:pem | filetype:key | filetype:ppk
      
 # Admin Panel and Login Page Discovery
  # Admin panels
        site:target.com inurl:admin
        site:target.com inurl:administrator
        site:target.com inurl:admin/login
        site:target.com inurl:cpanel
        site:target.com inurl:webmin
        site:target.com intitle:"admin" intitle:"login"
        site:target.com intitle:"dashboard" inurl:admin
        site:target.com inurl:wp-admin
        site:target.com inurl:administrator/index.php

# Login pages
       site:target.com inurl:login | inurl:signin | inurl:auth
       site:target.com intitle:"login" | intitle:"sign in"
       site:target.com inurl:user/login
       site:target.com inurl:account/login

# Registration pages
      site:target.com inurl:register | inurl:signup | inurl:join
      site:target.com intitle:"register" | intitle:"sign up" | intitle:"create account"

# Password reset
     site:target.com inurl:forgot | inurl:reset | inurl:recover
     site:target.com intitle:"forgot password" | intitle:"reset password"

 # Vulnerability Discovery Dorks    
  # SQL Injection indicators
        site:target.com inurl:id= | inurl:pid= | inurl:category= | inurl:item=
         site:target.com inurl:".php?id="
         site:target.com "sql syntax" | "mysql_fetch" | "unclosed quotation"
         site:target.com "ORA-" | "Oracle error"
          site:target.com "Microsoft OLE DB Provider"
         site:target.com "PostgreSQL query failed"
         site:target.com "Warning: mysql_" | "Warning: pg_"

# XSS indicators
        site:target.com inurl:q= | inurl:search= | inurl:query= | inurl:keyword=
       site:target.com inurl:redirect= | inurl:url= | inurl:return= | inurl:next=

# Directory listing
       site:target.com intitle:"index of"
       site:target.com intitle:"directory listing"
       site:target.com intitle:"parent directory"

# Error messages
        site:target.com "Fatal error" | "Parse error" | "Syntax error"
        site:target.com "stack trace" | "traceback" | "debugging"
         site:target.com "Warning:" "on line"
         site:target.com intext:"Exception in thread"

# Exposed services
        site:target.com intitle:"phpMyAdmin"
        site:target.com intitle:"Adminer"
        site:target.com intitle:"pgAdmin"
        site:target.com inurl:phpmyadmin
        site:target.com intitle:"Kibana"
        site:target.com intitle:"Grafana"
        site:target.com intitle:"Jenkins"
        site:target.com intitle:"GitLab"
#  API and Documentation Discovery
       site:target.com inurl:swagger | inurl:api-docs | inurl:openapi
       site:target.com filetype:json "openapi" | "swagger"
       site:target.com intitle:"Swagger UI"
       site:target.com inurl:graphql | inurl:graphiql
       site:target.com inurl:api/v1 | inurl:api/v2 | inurl:api/v3
       site:target.com filetype:yaml "paths:" "info:"
       site:target.com inurl:apidocs | inurl:api-reference

# Development/staging environments
      site:target.com inurl:dev | inurl:staging | inurl:test | inurl:uat
      site:target.com inurl:beta | inurl:alpha | inurl:sandbox
      site:*.dev.target.com
       site:*.staging.target.com
      site:*.test.target.com

# Internal documentation
      site:target.com filetype:pdf "internal" | "confidential" | "draft"
       site:target.com filetype:doc | filetype:docx "internal use only"
       site:target.com filetype:xlsx "employee" | "salary" | "password"

# GitHub OSINT
    # GitHub Dorking - search for secrets in code
     Organization-wide search
      org:target-org password
      org:target-org secret
      org:target-org api_key
      org:target-org token
      org:target-org AWS_ACCESS_KEY
      org:target-org private_key
      org:target-org credentials

# Specific file searches
     org:target-org filename:.env
     org:target-org filename:wp-config.php
     org:target-org filename:configuration.php
     org:target-org filename:config.py
     org:target-org filename:.htpasswd
     org:target-org filename:id_rsa
     org:target-org filename:shadow
     org:target-org filename:credentials
     org:target-org filename:docker-compose.yml

# Extension searches
      org:target-org extension:pem
      org:target-org extension:key
      org:target-org extension:env
      org:target-org extension:sql

# Automated GitHub dorking tools
# GitDorker
      python3 GitDorker.py -t $GITHUB_TOKEN -org target-org -d dorks/medium_dorks.txt

# truffleHog - find secrets in git history
      trufflehog github --org=target-org --json > trufflehog_results.json

# gitleaks
     gitleaks detect --source=/path/to/repo --report-path=gitleaks_report.json

# git-secrets
      git secrets --scan

# shhgit - find secrets in real-time
     shhgit --search-query "target.com"
        
# Social Media OSINT
     # LinkedIn reconnaissance
# Search: "target company" employees
    Extract: names, roles, technologies mentioned
    Job postings reveal: tech stack, internal tools, security measures

# Name to email generatio first.last@target.com
 firstlast@target.com
 flast@target.com
  first@target.com

# Tools:
# linkedin2username
 python3 linkedin2username.py -c "Target Company" -d target.com

# CrossLinked
    crosslinked -f '{first}.{last}@target.com' -t 'Target Company' -j 2

# Email verification
    emailhippo.com
    hunter.io/email-verifier

# Twitter/X OSINT
     Search for @target_company
     Monitor employee tweets about technology
     Search for leaked info: "target.com" "password"

# Instagram, Facebook (company pages)
     Employee posts revealing office setup, badge designs, etc.


 # OSINT Frameworks and Tools    
        # theHarvester - multi-source OSINT
theHarvester -d target.com -b all -l 500

# Sources: google, bing, linkedin, twitter, virustotal,
    certspotter, crtsh, rapiddns, sublist3r, etc.

# Recon-ng - OSINT framework
recon-ng
    [recon-ng][default] > marketplace install all
    [recon-ng][default] > workspaces create target
    [recon-ng][target] > modules search
    [recon-ng][target] > modules load recon/domains-hosts/google_site_web
    recon-ng][target] > options set SOURCE target.com
    [recon-ng][target] > run

# SpiderFoot - automated OSINT
     spiderfoot -s target.com -o output.html
     Web UI: spiderfoot -l 127.0.0.1:5001

# Maltego - visual link analysis
     Community edition available
     Transform-based OSINT

# OSINT Framework
     https://osintframework.com - comprehensive tool directory

# Shodan
     shodan search "hostname:target.com"
     shodan search "org:\"Target Organization\""
     shodan search "ssl.cert.subject.cn:target.com"

# Censys
      https://search.censys.io


# Automated OSINT Pipeline      
      #!/bin/bash
# osint_pipeline.sh
   TARGET=$1
   OUTDIR="recon/${TARGET}/osint"
   mkdir -p $OUTDIR

   echo "=== OSINT Pipeline: $TARGET ==="

    theHarvester
    echo "[*] Running theHarvester..."
    theHarvester -d $TARGET -b google,bing,crtsh,virustotal,rapiddns -l 500 \
    -f $OUTDIR/harvester 2>/dev/null

 Check for exposed git repos
     echo "[*] Checking for exposed .git..."
     for sub in $(cat recon/$TARGET/subdomains/all_subdomains.txt 2>/dev/null); do
      code=$(curl -s -o /dev/null -w "%{http_code}" "https://$sub/.git/config" 2>/dev/null)
    if [ "$code" = "200" ]; then
        echo "[+] Exposed .git found: https://$sub/.git/" >> $OUTDIR/exposed_git.txt
    fi
done

 Check for sensitive files
      echo "[*] Checking for sensitive files..."
      SENSITIVE_PATHS=".env .env.bak wp-config.php.bak .htpasswd .DS_Store
      config.php.bak web.config.bak phpinfo.php info.php server-status
      elmah.axd trace.axd .svn/entries crossdomain.xml"
      for path in $SENSITIVE_PATHS; do
      code=$(curl -s -o /dev/null -w "%{http_code}" "https://$TARGET/$path" 2>/dev/null)
      if [ "$code" = "200" ]; then
          echo "[+] Found: https://$TARGET/$path" >> $OUTDIR/sensitive_files.txt
       fi
done

 robots.txt and sitemap analysis
       echo "[*] Analyzing robots.txt and sitemap..."
       curl -s "https://$TARGET/robots.txt" > $OUTDIR/robots.txt 2>/dev/null
       curl -s "https://$TARGET/sitemap.xml" > $OUTDIR/sitemap.xml 2>/dev/null
   
 Extract disallowed paths from robots.txt
     grep "Disallow:" $OUTDIR/robots.txt 2>/dev/null | awk '{print $2}' > $OUTDIR/disallowed_paths.txt

    echo "[*] OSINT pipeline complete. Results in $OUTDIR/"
    
