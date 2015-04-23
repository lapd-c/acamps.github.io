{% set highlight bash %}
# An example hook script to verify what is about to be pushed.  Called by "git
# push" after it has checked the remote status, but before anything has been
# pushed.  If this script exits with a non-zero status nothing will be pushed.
#
# This hook is called with the following parameters:
#
# $1 -- Name of the remote to which the push is being done
# $2 -- URL to which the push is being done
#
# If pushing without using a named remote those arguments will be equal.
#
# Information about the commits which are being pushed is supplied as lines to
# the standard input in the form:
#
#   <local ref> <local sha1> <remote ref> <remote sha1>
#
# This sample shows how to prevent push of commits where the log message starts
# with "WIP" (work in progress).

forbidden_words=["echo","print_r","var_dump"]
# The following list could be expanded
declare -a forbidden_words=("echo" "print_r" "var_dump")
num_modified_files=$(git diff $1 --name-only | wc -l)
if [ "$num_modified_files" -gt 0 ]
then
    sum=0
        for word in "${forbidden_words[@]}"
        do
        amount=$(cat `git diff $1 --name-only` | grep $word | wc -w)
        cat `git diff $1 --name-only` | grep $word | wc -w
        echo $1
        sum=$(($sum+$amount))
    done
    if [ "$sum" -gt 0 ]
    then
        echo "There are some forbidden words in your code. Check them before pushing."
        # Exit code different than 0 is considered error in bash
        exit 1
    else
        echo "Your code looks ok. Proceeding to commit."
        # Exit code considered ok.
        exit 0
    fi
fi
{% endhighlight %}
